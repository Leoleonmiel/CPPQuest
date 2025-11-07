# 13. Debugage C++ avancé  
*(Advanced C++ Debugging: deadlocks, UB, move, const, constexpr, templates, atomics, linking)*

## 13.1 Concurrence, verrous, atomiques

### 13.1.1 Deadlock basique (ordre de verrous)
Expliquez le blocage potentiel et réécrivez sans interblocage.
```cpp
std::mutex m1, m2;

void f() {
    std::lock_guard<std::mutex> L1(m1);
    std::this_thread::sleep_for(std::chrono::milliseconds(1));
    std::lock_guard<std::mutex> L2(m2);
}

void g() {
    std::lock_guard<std::mutex> L2(m2);
    std::this_thread::sleep_for(std::chrono::milliseconds(1));
    std::lock_guard<std::mutex> L1(m1);
}

int main() {
    std::thread t1(f), t2(g);
    t1.join(); t2.join();
}
```
---

### 13.1.2 Double-checked locking incorrect
Identifiez la condition de data race et proposez une solution sûre.
```cpp
struct Obj { int x = 42; };
Obj* G = nullptr;
std::mutex M;

Obj* get() {
    if (G == nullptr) {
        std::lock_guard<std::mutex> lk(M);
        if (G == nullptr) G = new Obj;
    }
    return G;
}
```
---

### 13.1.3 ABA avec atomiques
Expliquez le problème ABA et proposez des stratégies d’atténuation.
```cpp
std::atomic<int*> head{nullptr};
// Supposer une pile lock-free pop/push basée sur CAS sur head.
```
---

### 13.1.4 memory_order inadapté
Que peut-il se passer ici et pourquoi ? Corrigez.
```cpp
std::atomic<bool> ready{false};
int data = 0;

void producer() {
    data = 123;
    ready.store(true, std::memory_order_relaxed);
}

void consumer() {
    while (!ready.load(std::memory_order_relaxed)) {}
    printf("%d\n", data);
}
```
---

### 13.1.5 Contention de mutex et faux partage
Pourquoi cette approche est-elle lente ? Proposez des améliorations.
```cpp
struct alignas(64) Counter { std::atomic<int> v{0}; };
Counter c;

void worker() {
    for (int i=0;i<1'000'000;++i) c.v.fetch_add(1, std::memory_order_relaxed);
}

int main() {
    std::thread t1(worker), t2(worker), t3(worker), t4(worker);
    t1.join(); t2.join(); t3.join(); t4.join();
}
```
---

## 13.2 Durée de vie, UB, aliasing, itérateurs

### 13.2.1 Dangling reference après reallocation
Identifiez l’UB et corrigez.
```cpp
std::vector<int> v{1,2,3};
int& r = v[0];
v.push_back(4);
int x = r; // valide ?
```
---

### 13.2.2 string_view pendant mutation
Expliquez le piège et donnez une alternative sûre.
```cpp
std::string s = "abcdef";
std::string_view sv = s;
s.push_back('x');
char c = sv[0];
```
---

### 13.2.3 use-after-free via unique_ptr::release
Localisez le bug.
```cpp
std::unique_ptr<int> p = std::make_unique<int>(5);
int* raw = p.release(); // ownership perdu
// ...
delete raw;
delete raw; // double free latent ?
```
---

### 13.2.4 strict aliasing UB
Pourquoi ceci est UB ? Corrigez.
```cpp
float f = 1.0f;
int* pi = reinterpret_cast<int*>(&f);
int bits = *pi;
```
---

### 13.2.5 Itérateurs invalidés
Qu’affiche ce programme ? Corrigez.
```cpp
std::vector<int> v{1,2,3,4,5};
for (auto it = v.begin(); it != v.end(); ++it) {
    if (*it % 2 == 0) v.erase(it);
}
for (int x : v) std::cout << x << " ";
```
---

## 13.3 Move, const-correctness, RVO, noexcept

### 13.3.1 Move elidé vs interdit par noexcept
Expliquez le comportement et optimisez.
```cpp
struct Big {
    Big();
    Big(const Big&);
    Big(Big&&) noexcept(false);
};

Big make() {
    Big b;
    return b; // copie forcée ?
}
```
---

### 13.3.2 Move-from const
Pourquoi `std::move` ne bouge pas ici ?
```cpp
void use(const std::string& s) {
    std::string t = std::move(s);
    // ...
}
```
---

### 13.3.3 Règle des cinq oubliée
Trouvez le bug de double-free potentiel.
```cpp
struct Buf {
    size_t n;
    char* p;
    Buf(size_t n): n(n), p(new char[n]) {}
    ~Buf(){ delete[] p; }
};

Buf makeB(size_t k) {
    Buf b(k);
    return b;
}
```
---

### 13.3.4 noexcept sur move
Quand faut-il marquer le move constructor `noexcept` et pourquoi ?
```cpp
struct T {
    T(const T&);
    T(T&&) noexcept(/* ? */);
    std::vector<int> v;
};
```
---

### 13.3.5 const-correctness et overload résolution
Expliquez la résolution d’appel.
```cpp
struct S {
    void foo() & { puts("&"); }
    void foo() && { puts("&&"); }
};

S makeS();
int main() {
    S s;
    s.foo();
    makeS().foo();
}
```
---

## 13.4 constexpr, templates, SFINAE/constraints, ODR

### 13.4.1 constexpr mal employé
Pourquoi ceci échoue-t-il parfois ?
```cpp
constexpr int f(bool b) {
    int x = 0;
    if (b) {
        static int y = 1; // autorisé ?
        x += y;
    }
    return x;
}
```
---

### 13.4.2 SFINAE raté
Rendre `print_int` activable uniquement pour types entiers.
```cpp
template<class T>
void print_int(T x) {
    static_assert(std::is_integral_v<T>, "integers only");
    std::cout << x << "\n";
}
```
---

### 13.4.3 Concepts et ambiguïté
Résolvez le conflit d’overload.
```cpp
template<class T> concept Addable = requires(T a){ a + a; };

template<Addable T>
void f(T){ puts("Addable"); }

template<class T>
void f(T){ puts("Generic"); }

int main(){ f(3); f(std::string{"x"}); }
```
---

### 13.4.4 One Definition Rule (ODR)
Identifiez la violation ODR et proposez un remède.
```cpp
/// a.hpp
inline int g() { static int x = 0; return ++x; }

/// b.hpp
int g(); // signature différente dans l’édition finale ?
```
---

### 13.4.5 static init order fiasco
Expliquez le risque et proposez une solution.
```cpp
extern std::string A();
static std::string G = A(); // ordre d’init global inter-TU
```
---

## 13.5 Exceptions, garanties, ressources, construction

### 13.5.1 Slicing et polymorphisme
Où est le slicing et comment l’éviter ?
```cpp
struct Base { virtual ~Base(){} };
struct Der: Base { int x = 42; };

void h(Base b) {
    // ...
}

int main() {
    Der d;
    h(d);
}
```
---

### 13.5.2 Exception safety forte
Rendez cette opération “strong exception safe”.
```cpp
struct Vec {
    std::vector<int> v;
    void append(const std::vector<int>& w) {
        for (int x: w) v.push_back(x);
    }
};
```
---

### 13.5.3 RAII manquant
Localisez la fuite possible en cas d’exception.
```cpp
void read_file(const char* path) {
    FILE* f = fopen(path, "rb");
    std::vector<char> buf(1024*1024);
    if (!f) throw std::runtime_error("open");
    if (fread(buf.data(),1,buf.size(),f) < buf.size()) throw std::runtime_error("io");
    fclose(f);
}
```
---

### 13.5.4 noexcept et terminaisons
Que se passe-t-il ici et pourquoi ?
```cpp
void g() noexcept {
    throw std::runtime_error("boom");
}

int main() {
    try { g(); } catch(...) { puts("caught"); }
}
```
---

### 13.5.5 vtable pendant construction
Quel `Print()` est appelé et pourquoi ?
```cpp
struct A { A(){ Print(); } virtual void Print(){ puts("A"); } virtual ~A(){} };
struct B: A { B(){ } void Print() override { puts("B"); } };

int main(){ B b; }
```
---

## 13.6 Performances, allocation, alignement, IoC

### 13.6.1 Allocations excessives
Optimisez en réduisant les réallocations.
```cpp
std::vector<std::string> V;
for (int i=0;i<1'000'000;++i)
    V.push_back(std::to_string(i));
```
---

### 13.6.2 Alignement requis
Expliquez le comportement indéfini potentiel.
```cpp
struct alignas(32) M { float a[8]; };
std::byte buf[sizeof(M)];
M* p = new (buf) M; // placement-new
float* pf = p->a;   // alignement garanti ?
```
---

### 13.6.3 aliasing strict avec std::byte
Pourquoi est-ce plus sûr avec std::byte qu’avec char* ?
```cpp
void fill(void* p, size_t n) {
    auto b = static_cast<std::byte*>(p);
    for (size_t i=0;i<n;++i) b[i] = std::byte{0xFF};
}
```
---

### 13.6.4 ADL piège
Expliquez la résolution et comment la contrôler.
```cpp
namespace lib { struct X{}; void swap(X&,X&){ puts("lib::swap"); } }
void swap(lib::X&, lib::X&){ puts("::swap"); }

int main(){
    lib::X a,b;
    using std::swap;
    swap(a,b);
}
```
---

### 13.6.5 Erreurs d’injection de dépendance
Pourquoi ce design nuit-il au test et aux perfs ? Proposez mieux.
```cpp
struct Service {
    static Service& instance();
    int run();
};

int foo() {
    return Service::instance().run();
}
```
---

## 13.7 Métaprogrammation, construction, liaisons

### 13.7.1 Perfect forwarding incorrect
Corrigez la déduction et la transmission.
```cpp
template<class T, class... Args>
std::unique_ptr<T> make(Args... args) {
    return std::unique_ptr<T>(new T(args...));
}
```
---

### 13.7.2 Dépendance de type et lookup
Pourquoi ce code ne compile-t-il pas ? Corrigez avec `typename`/`template`.
```cpp
template<class T>
struct C {
    using It = typename T::iterator;
    void f(T& t){
        It it = t.begin();
        // t::template g<int>(); // appel dépendant ?
    }
};
```
---

### 13.7.3 Lvalue/rvalue overload set
Expliquez la sélection et donnez une API stable.
```cpp
struct S {
    std::string get() &  { return "l"; }
    std::string get() && { return "r"; }
};

S make();
auto a = S{}.get();
S s;
auto b = s.get();
```
---

## 13.8 Build, linking, visibilité

### 13.8.1 ODR-USE et inline variables
Expliquez pourquoi cette variable doit être `inline`.
```cpp
/// header.hpp
std::string kName = "X";
```
---

### 13.8.2 Visibilité des symboles et LTO
Pourquoi ce symbole fuite-t-il et comment le restreindre ?
```cpp
// lib.cpp
extern "C" int Internal() { return 42; }
```
---

### 13.8.3 Mismatch d’ABI entre librairies
Quels symptômes et comment prévenir ?
```cpp
// Une lib construite avec autre standard lib / autre flags (e.g. _GLIBCXX_USE_CXX11_ABI)
```
---

