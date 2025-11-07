# 17. Adressage avancé et bas-niveau  
*(Advanced and Low-Level Addressing)*  

---

## 17.1 Casts et conversions de pointeurs / Pointer Casting and Conversion  

### 17.1.1  
Expliquez ce que fait ce `reinterpret_cast`.
```cpp
int a = 65;
char* p = reinterpret_cast<char*>(&a);
std::cout << *p;
```
---

### 17.1.2  
Quelle est la différence entre `static_cast`, `reinterpret_cast`, et `const_cast` ?

---

### 17.1.3  
Analysez le comportement suivant.
```cpp
float f = 3.14f;
int* ip = reinterpret_cast<int*>(&f);
std::cout << *ip;
```
---

### 17.1.4  
Pourquoi ce code provoque-t-il un comportement indéfini ?
```cpp
int a = 1;
float* b = reinterpret_cast<float*>(&a);
*b = 2.5f;
```
---

### 17.1.5  
Quelle est la signification du “strict aliasing rule” en C++ ?  

---

## 17.2 Offsets mémoire et structures / Memory Offsets and Structs  

### 17.2.1  
Quelle est la valeur imprimée ici ?
```cpp
struct S {
    int a;
    double b;
    char c;
};

std::cout << offsetof(S, b);
```
---

### 17.2.2  
Que retourne ce calcul d’adresse ?
```cpp
struct Data { int x; int y; };
Data d{5,10};
char* p = reinterpret_cast<char*>(&d);
int* next = reinterpret_cast<int*>(p + sizeof(int));
std::cout << *next;
```
---

### 17.2.3  
Expliquez ce que fait ce pointer arithmetic.
```cpp
struct Point { float x, y; };
Point arr[3];
Point* p = arr;
p++;
std::cout << (p - arr);
```
---

### 17.2.4  
Pourquoi `reinterpret_cast` doit être utilisé avec prudence pour naviguer dans la mémoire brute ?  

---

### 17.2.5  
Quel est l’effet de l’alignement sur les offsets mémoire ?  

---

## 17.3 Alignement et padding / Alignment and Padding  

### 17.3.1  
Pourquoi la taille de cette structure n’est-elle pas la somme des champs ?
```cpp
struct X {
    char a;
    int b;
    char c;
};
```
---

### 17.3.2  
Quel est l’effet de `alignas(16)` ici ?
```cpp
struct alignas(16) Vec4 { float x,y,z,w; };
```
---

### 17.3.3  
Quelle est la différence entre alignement naturel et alignement forcé ?  

---

### 17.3.4  
Expliquez la fonction `std::align`.

---

### 17.3.5  
Que garantit `std::aligned_storage` ?  

---

## 17.4 Pointeurs génériques et aliasing / Generic Pointers and Aliasing  

### 17.4.1  
Analysez ce code utilisant un `void*`.
```cpp
int a = 5;
void* vp = &a;
int* ip = static_cast<int*>(vp);
std::cout << *ip;
```
---

### 17.4.2  
Pourquoi `void*` ne peut pas être déréférencé directement ?  

---

### 17.4.3  
Expliquez la différence entre `reinterpret_cast` et `std::bit_cast`.

---

### 17.4.4  
Que fait ce code ?
```cpp
struct A { int x; };
A a{42};
char* raw = reinterpret_cast<char*>(&a);
raw[0] = 0;
std::cout << a.x;
```
---

### 17.4.5  
Pourquoi `memcpy` peut être utilisé pour contourner les règles d’aliasing ?  

---

## 17.5 Smart pointers et ownership / Smart Pointers and Ownership  

### 17.5.1  
Que garantit `std::unique_ptr` concernant la possession d’un objet ?

---

### 17.5.2  
Expliquez le comportement suivant.
```cpp
#include <memory>
#include <iostream>

int main() {
    std::unique_ptr<int> p = std::make_unique<int>(5);
    std::unique_ptr<int> q = std::move(p);
    std::cout << *q;
}
```
---

### 17.5.3  
Pourquoi `unique_ptr` n’est-il pas copiable ?  

---

### 17.5.4  
Comment partager un objet entre plusieurs pointeurs avec `std::shared_ptr` ?

---

### 17.5.5  
Que fait `std::weak_ptr` et pourquoi est-il nécessaire ?  

---

### 17.5.6  
Quel problème survient ici ?
```cpp
#include <memory>

struct Node {
    std::shared_ptr<Node> next;
};

int main() {
    auto a = std::make_shared<Node>();
    auto b = std::make_shared<Node>();
    a->next = b;
    b->next = a;
}
```
---

### 17.5.7  
Comment résoudre la boucle de références circulaires précédente ?  

---

### 17.5.8  
Que fait ce code avec un deleter personnalisé ?
```cpp
#include <memory>
#include <iostream>

void customDelete(int* p) {
    std::cout << "Deleting " << *p;
    delete p;
}

int main() {
    std::unique_ptr<int, decltype(&customDelete)> ptr(new int(10), customDelete);
}
```
---

### 17.5.9  
Quelle est la différence entre `reset()` et `release()` sur `unique_ptr` ?

---

### 17.5.10  
Pourquoi est-il dangereux d’obtenir un pointeur brut depuis un `unique_ptr` ?  

---

## 17.6 Gestion mémoire bas-niveau / Low-Level Memory Management  

### 17.6.1  
Quel est le rôle de `std::launder` en C++17 ?  

---

### 17.6.2  
Expliquez la différence entre `placement new` et `operator new`.
```cpp
char buffer[sizeof(int)];
int* p = new (buffer) int(9);
```
---

### 17.6.3  
Que se passe-t-il ici ?
```cpp
int* p = static_cast<int*>(::operator new(sizeof(int)));
*p = 5;
::operator delete(p);
```
---

### 17.6.4  
Pourquoi est-il important de faire correspondre `new[]` avec `delete[]` ?  

---

### 17.6.5  
Quel est l’impact du *memory alignment* sur les performances SIMD ?  

---

## 17.7 Pointeurs sur membres virtuels et adresses dynamiques / Virtual and Dynamic Member Pointers  

### 17.7.1  
Que contient réellement un pointeur sur fonction virtuelle ?

struct Base { virtual void f() {} };
void (Base::*fp)() = &Base::f;

---

### 17.7.2  
Que se passe-t-il si on appelle une méthode virtuelle via un pointeur incorrect ?  

---

### 17.7.3  
Expliquez comment obtenir l’adresse réelle d’une méthode virtuelle dans une vtable (sans exécution).  

---

### 17.7.4  
Pourquoi `reinterpret_cast` d’un pointeur de fonction virtuelle est-il non portable ?  

---

### 17.7.5  
Comment le compilateur gère-t-il l’adressage multiple en héritage virtuel ?  

---