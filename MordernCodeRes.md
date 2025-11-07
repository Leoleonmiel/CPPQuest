# 14. C++20 / C++23 — Lecture et compréhension de code moderne  

## 14.1  
Quel est le comportement attendu de ce programme utilisant les modules ?
```cpp
export module math;

export int add(int a, int b) { return a + b; }

import math;
int main() {
    int x = add(2, 3);
    return x;
}
```
---

## 14.2  
Que fait exactement ce code avec `constexpr` et `consteval` ?
```cpp
consteval int Square(int x) { return x * x; }

constexpr int Power(int x) {
    return Square(x);
}

int main() {
    constexpr int v = Power(4);
    return v;
}
```
---

## 14.3  
Quel sera le résultat et pourquoi ?
```cpp
#include <print>

int main() {
    std::print("Value: {}\n", 42);
}
```
---

## 14.4  
Quel est le rôle de `std::move_only_function` ici ?
```cpp
#include <functional>
#include <iostream>

void run(std::move_only_function<void()> f) { f(); }

int main() {
    int v = 42;
    run([x = v]() { std::cout << x; });
}
```
---

## 14.5  
Que se passe-t-il si ce code est exécuté ?
```cpp
#include <ranges>
#include <vector>
#include <iostream>

int main() {
    std::vector<int> v{1,2,3,4,5};
    for (int i : v | std::views::filter([](int x){ return x % 2; })
                   | std::views::transform([](int x){ return x * x; }))
        std::cout << i << " ";
}
```
---

## 14.6  
Analysez la capture et l’évaluation différée.
```cpp
#include <iostream>

int main() {
    int a = 10;
    auto f = [x = a + 5]() { return x; };
    a = 20;
    std::cout << f();
}
```
---

## 14.7  
Quel est l’effet de `std::atomic_ref` ici ?
```cpp
#include <atomic>
#include <iostream>

int main() {
    int counter = 0;
    std::atomic_ref<int> ref(counter);
    ref.fetch_add(5);
    std::cout << counter;
}
```
---

## 14.8  
Qu’affiche ce code exploitant `std::expected` ?
```cpp
#include <expected>
#include <iostream>

std::expected<int, const char*> compute(bool ok) {
    if (ok) return 10;
    return std::unexpected("error");
}

int main() {
    auto r = compute(false);
    if (r) std::cout << *r;
    else std::cout << r.error();
}
```
---

## 14.9  
Quel est le comportement ici avec `constexpr std::string` ?
```cpp
#include <string>

constexpr auto make() {
    std::string s = "abc";
    s += "def";
    return s;
}

int main() {
    constexpr auto x = make();
}
```
---

## 14.10  
Comment ce programme compile-t-il avec `co_await` ?
```cpp
#include <coroutine>
#include <iostream>

struct Task {
    struct promise_type {
        Task get_return_object() { return {}; }
        std::suspend_never initial_suspend() noexcept { return {}; }
        std::suspend_never final_suspend() noexcept { return {}; }
        void return_void() {}
        void unhandled_exception() {}
    };
};

Task foo() {
    std::cout << "Running\n";
    co_return;
}

int main() {
    foo();
}
```
---

## 14.11  
Quel sera l’output produit ?
```cpp
#include <utility>
#include <iostream>

int main() {
    auto [a, b] = std::pair(10, 20);
    std::cout << a + b;
}
```
---

## 14.12  
Quel est le résultat logique de ce pattern matching ?
```cpp
#include <variant>
#include <iostream>

int main() {
    std::variant<int, std::string> v = "test";
    std::visit([](auto&& arg) {
        std::cout << arg;
    }, v);
}
```
---

## 14.13  
Analysez le comportement du code suivant.
```cpp
#include <optional>
#include <iostream>

std::optional<int> get(bool ok) {
    if (ok) return 5;
    return std::nullopt;
}

int main() {
    auto v = get(false).value_or(42);
    std::cout << v;
}
```
---

## 14.14  
Quelle est la différence fonctionnelle ici ?
```cpp
#include <ranges>
#include <vector>
#include <iostream>

int main() {
    std::vector<int> v{1,2,3,4};
    auto r = v | std::views::drop(1);
    for (int i : r) std::cout << i;
}
```
---

## 14.15  
Que fait ce code exploitant `std::thread::request_stop` ?
```cpp
#include <thread>
#include <iostream>

void worker(std::stop_token st) {
    while (!st.stop_requested()) std::cout << ".";
}

int main() {
    std::jthread t(worker);
    std::this_thread::sleep_for(std::chrono::milliseconds(10));
}
```
---

## 14.16  
Quel est le comportement exact de cette construction avec `concept` ?
```cpp
template<typename T>
concept Integral = std::is_integral_v<T>;

void print(Integral auto v) { std::cout << v; }

int main() { print(123); }
```
---

## 14.17  
Que produit ce code avec `std::generator` ?
```cpp
#include <generator>
#include <iostream>

std::generator<int> numbers() {
    for (int i = 0; i < 3; ++i)
        co_yield i;
}

int main() {
    for (int x : numbers())
        std::cout << x;
}
```
---

## 14.18  
Comment ce code se comporte-t-il avec `if consteval` ?
```cpp
#include <iostream>

constexpr int square(int x) { return x * x; }

int test(int x) {
    if consteval { return square(x); }
    else { return x; }
}

int main() { std::cout << test(3); }
```
---

## 14.19  
Quel est le comportement de cette fonction `constinit` ?
```cpp
constinit int value = 10;

int main() {
    value += 5;
    return value;
}
```
---

## 14.20  
Analysez la sémantique et le résultat final.
```cpp
#include <print>
#include <string>

int main() {
    std::string s = "C++23";
    std::print("{} rocks\n", s);
}
```
## 14.21  
Que fait ce programme utilisant des modules partitionnés ?
```cpp
export module math:core;
export int mul(int a, int b) { return a * b; }

export module math:extra;
import :core;
export int square(int x) { return mul(x, x); }

import math:extra;
int main() { return square(5); }
```
---

## 14.22  
Analysez le comportement de cette coroutine avec `co_yield`.
```cpp
#include <coroutine>
#include <iostream>

struct Generator {
    struct promise_type {
        int value;
        Generator get_return_object() { return Generator{this}; }
        std::suspend_always initial_suspend() noexcept { return {}; }
        std::suspend_always yield_value(int v) { value = v; return {}; }
        std::suspend_always final_suspend() noexcept { return {}; }
        void return_void() {}
        void unhandled_exception() {}
    };
    promise_type* p;
    Generator(promise_type* p): p(p) {}
    bool next() { return p->yield_value(0), true; }
    int current() const { return p->value; }
};

Generator gen() { co_yield 7; co_yield 8; }

int main() {
    auto g = gen();
    g.next(); std::cout << g.current();
}
```
---

## 14.23  
Quel est le comportement du code avec `std::mdspan` ?
```cpp
#include <mdspan>
#include <array>
#include <iostream>

int main() {
    std::array<float, 6> data{1,2,3,4,5,6};
    std::mdspan<float, std::extents<2,3>> mat(data.data());
    for (int i=0;i<2;i++) {
        for (int j=0;j<3;j++)
            std::cout << mat(i,j) << " ";
        std::cout << "\n";
    }
}
```
---

## 14.24  
Comment s’exécute ce code avec `std::execution::par` ?
```cpp
#include <vector>
#include <numeric>
#include <execution>
#include <iostream>

int main() {
    std::vector<int> v(1000);
    std::iota(v.begin(), v.end(), 1);
    long long sum = std::reduce(std::execution::par, v.begin(), v.end(), 0LL);
    std::cout << sum;
}
```
---

## 14.25  
Que démontre ce code utilisant `std::barrier` ?
```cpp
#include <barrier>
#include <thread>
#include <iostream>

std::barrier sync(3);

void worker(int id) {
    std::cout << "Before " << id << "\n";
    sync.arrive_and_wait();
    std::cout << "After " << id << "\n";
}

int main() {
    std::thread a(worker,1), b(worker,2), c(worker,3);
    a.join(); b.join(); c.join();
}
```
---

## 14.26  
Quel est le résultat logique de cette exécution concurrente ?
```cpp
#include <latch>
#include <thread>
#include <iostream>

std::latch start(3);

void job(int id) {
    start.count_down();
    start.wait();
    std::cout << id;
}

int main() {
    std::thread t1(job,1), t2(job,2), t3(job,3);
    t1.join(); t2.join(); t3.join();
}
```
---

## 14.27  
Comment ce code utilise `std::format_to` ?
```cpp
#include <format>
#include <string>
#include <vector>
#include <iostream>

int main() {
    std::string out;
    std::format_to(std::back_inserter(out), "Result: {}\n", 1234);
    std::cout << out;
}
```
---

## 14.28  
Analysez le comportement de `std::atomic_wait` ici.
```cpp
#include <atomic>
#include <thread>
#include <iostream>

std::atomic<int> value{0};

void waiter() {
    value.wait(0);
    std::cout << "wakeup";
}

int main() {
    std::thread t(waiter);
    std::this_thread::sleep_for(std::chrono::milliseconds(5));
    value.store(1);
    value.notify_one();
    t.join();
}
```
---

## 14.29  
Quelle est la sortie attendue du programme suivant avec `std::expected` ?
```cpp
#include <expected>
#include <iostream>

std::expected<int, std::string> f(bool ok) {
    if (ok) return 99;
    return std::unexpected("fail");
}

int main() {
    auto r = f(true);
    if (r) std::cout << *r;
    else std::cout << r.error();
}
```
---

## 14.30  
Quel est le comportement de ce code avec un `constexpr std::vector` ?
```cpp
#include <vector>
#include <algorithm>

constexpr auto make_vec() {
    std::vector<int> v{1,2,3};
    std::ranges::reverse(v);
    return v;
}

int main() {
    constexpr auto v = make_vec();
}
```
---

## 14.31  
Analysez ce code exploitant un `deducing this`.

#include <iostream>
```cpp
struct Acc {
    int sum{0};
    void add(this Acc& self, int x) { self.sum += x; }
};

int main() {
    Acc a;
    a.add(5);
    std::cout << a.sum;
}
```
---
```cpp
## 14.32  
Quel est l’effet de la contrainte `requires` ici ?

#include <iostream>
#include <concepts>

template<typename T>
requires std::integral<T> && (sizeof(T) > 1)
void show(T v) { std::cout << v; }

int main() { show(256); }
```
---

## 14.33  
Que démontre ce code avec `constexpr virtual` ?
```cpp
struct Base {
    virtual constexpr int id() const { return 1; }
};

struct Der : Base {
    constexpr int id() const override { return 2; }
};

constexpr int test() {
    Der d;
    return d.id();
}

int main() {
    constexpr int v = test();
    return v;
}
```
---

## 14.34  
Quel est le résultat exact ?
```cpp
#include <ranges>
#include <vector>
#include <iostream>

int main() {
    std::vector<int> v{1,2,3,4,5,6};
    auto r = v | std::views::chunk(2);
    for (auto sub : r) {
        for (int x : sub) std::cout << x;
        std::cout << "-";
    }
}
```
---

## 14.35  
Que se passe-t-il dans ce code combinant `std::span` et const-correctness ?
```cpp
#include <span>
#include <array>
#include <iostream>

int main() {
    std::array<int,3> arr{1,2,3};
    std::span<const int> sp(arr);
    arr[0] = 10;
    std::cout << sp[0];
}
```
---

## 14.36  
Analysez la logique de ce `static constexpr auto lambda`.
```cpp
#include <iostream>

static constexpr auto L = [](int x){ return x*x; };

int main() {
    std::cout << L(5);
}
```
---

## 14.37  
Quel est le comportement de cette déclaration `explicit(true)` ?
```cpp
struct T {
    explicit(true) T(int) {}
};

int main() {
    T a = 5;
}
```
---

## 14.38  
Quel est le résultat de cette combinaison `constexpr` et `std::optional` ?
```cpp
#include <optional>

constexpr std::optional<int> f(bool b) {
    if (b) return 7;
    return std::nullopt;
}

int main() {
    constexpr auto r = f(false);
}
```
---

## 14.39  
Analysez la logique d’un `if consteval` imbriqué.
```cpp
constexpr int test(int x) {
    if consteval {
        return x * 2;
    } else {
        return x + 1;
    }
}

int main() { return test(10); }
```
---

## 14.40  
Que se passe-t-il ici avec `std::move_only_function` et capture mutable ?
```cpp
#include <functional>
#include <iostream>

int main() {
    int x = 5;
    std::move_only_function<void()> fn = [x = std::move(x)]() mutable {
        x++;
        std::cout << x;
    };
    fn();
}
```