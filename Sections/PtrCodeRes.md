# 16. Adressage, pointeurs et références  
*(Addressing, Pointers, and References)*  

---

## 16.1 Adressage de base / Basic Addressing  

### 16.1.1  
Quelle est la différence entre `&x` et `*p` ?
```cpp
int x = 5;
int* p = &x;
int y = *p;
```
---

### 16.1.2  
Expliquez ce que font ces lignes de code.
```cpp
int a = 10;
int* b = &a;
int** c = &b;
**c = 20;
```
---

### 16.1.3  
Quelle est la valeur finale de `x` et `y` ?
```cpp
int x = 3;
int* p = &x;
int y = *p;
*p = 7;
```
---

### 16.1.4  
Analysez ce passage de paramètres.

void modify(int* p) { *p = 99; }
```cpp
int main() {
    int v = 10;
    modify(&v);
}
```
---

### 16.1.5  
Que se passe-t-il si `p` n’est pas initialisé ?
```cpp
int* p;
*p = 1;
```
---

## 16.2 Références et const / References and Const  

### 16.2.1  
Quelle est la différence entre une référence et un pointeur ?
```cpp
int x = 42;
int& r = x;
int* p = &x;
```
---

### 16.2.2  
Peut-on réassigner une référence ?
```cpp
int a = 1, b = 2;
int& r = a;
r = b;
```
---

### 16.2.3  
Expliquez ce qui se passe ici avec `const`.
```cpp
int x = 10;
const int* p = &x;
*p = 20;
```
---

### 16.2.4  
Quelle est la différence entre `const int*` et `int* const` ?
```cpp
int x = 5, y = 9;
const int* p1 = &x;
int* const p2 = &y;
```
---

### 16.2.5  
Que fait ce code avec `const_cast` ?
```cpp
const int n = 8;
int* p = const_cast<int*>(&n);
*p = 12;
```
---

## 16.3 Adressage multiple et pointeurs de pointeurs / Multi-level Addressing  

### 16.3.1  
Quelle est la valeur de `**pp` ?
```cpp
int x = 11;
int* p = &x;
int** pp = &p;
```
---

### 16.3.2  
Que modifie réellement cette fonction ?
```cpp
void update(int** pp) {
    **pp = 33;
}

int main() {
    int v = 7;
    int* p = &v;
    update(&p);
}
```
---

### 16.3.3  
Analysez l’adresse affichée.
```cpp
int x = 5;
int* p = &x;
std::cout << &p << " " << p;
```
---

### 16.3.4  
Quelle est la différence entre `int**` et `int*&` ?
```cpp
void test(int** p) {}
void testRef(int*& p) {}
```
---

### 16.3.5  
Expliquez le comportement suivant.
```cpp
int x = 4;
int* p = &x;
int** q = &p;
**q = 15;
```
---

## 16.4 Pointeurs et tableaux / Pointers and Arrays  

### 16.4.1  
Que fait exactement cette expression ?
```cpp
int arr[3] = {1,2,3};
int* p = arr;
int x = *(p + 1);
```
---

### 16.4.2  
Pourquoi `arr` et `&arr` ne sont-ils pas équivalents ?
```cpp
int arr[3];
std::cout << arr << " " << &arr;
```
---

### 16.4.3  
Analysez ce code et ses adresses.
```cpp
int v[2] = {5,10};
int* p1 = v;
int* p2 = &v[1];
```
---

### 16.4.4  
Que se passe-t-il ici ?
```cpp
char s[] = "abc";
char* p = s;
p[1] = 'z';
```
---

### 16.4.5  
Quelle est la différence entre `*(arr + i)` et `arr[i]` ?  

---

## 16.5 Pointeurs de fonction / Function Pointers  

### 16.5.1  
Comment fonctionne cet appel indirect ?
```cpp
void hello() { std::cout << "Hi"; }

int main() {
    void (*fptr)() = &hello;
    fptr();
}
```
---

### 16.5.2  
Expliquez le prototype de ce pointeur.
```cp
int add(int a, int b) { return a + b; }

int main() {
    int (*op)(int,int) = add;
    std::cout << op(2,3);
}
```
---

### 16.5.3  
Que fait cette fonction de callback ?
```cpp
void run(void (*cb)(int)) {
    cb(5);
}

void printInt(int x) { std::cout << x; }

int main() { run(printInt); }
```
---

### 16.5.4  
Comment stocker un pointeur de fonction dans une classe ?
```cpp
class Fun {
    int (*callback)(int);
public:
    Fun(int (*cb)(int)) : callback(cb) {}
    void exec() { std::cout << callback(3); }
};
```
---

### 16.5.5  
Expliquez comment `std::function` généralise les pointeurs de fonction.  

---

## 16.6 Allocation dynamique et pointeurs / Dynamic Allocation and Pointers  

### 16.6.1  
Que fait ce code en mémoire ?
```cpp
int* p = new int(42);
delete p;
```
---

### 16.6.2  
Quelle erreur logique contient ce code ?
```cpp
int* p = new int[5];
delete p;
```
---

### 16.6.3  
Pourquoi l’usage de `new` brut est déconseillé en C++ moderne ?  

---

### 16.6.4  
Que se passe-t-il ici ?
```cpp
int* p = new int(10);
int* q = p;
delete p;
*q = 9;
```
---

### 16.6.5  
Quelle est la différence entre `unique_ptr` et `shared_ptr` ?  

---

## 16.7 Pointeurs sur membres et this / Member Pointers and this  

### 16.7.1  
Analysez le fonctionnement du pointeur sur membre.  
```cpp
class A {
public:
    int value = 5;
    int get() const { return value; }
};

int main() {
    int A::* ptr = &A::value;
    A a;
    std::cout << a.*ptr;
}
```
---

### 16.7.2  
Comment appeler une méthode via un pointeur de fonction membre ?  
```cpp
class B {
public:
    void show() { std::cout << "ok"; }
};

int main() {
    void (B::*fptr)() = &B::show;
    B b;
    (b.*fptr)();
}
```
---

### 16.7.3  
Quelle est la valeur de `this` dans le constructeur suivant ?
```cpp
class C {
public:
    C() { std::cout << this; }
};

int main() { C c; }
```
---

### 16.7.4  
Expliquez la différence entre `this->x` et `(*this).x`.  

---

### 16.7.5  
Pourquoi les pointeurs sur membres ne peuvent pas être castés vers `void*` directement ?  

---