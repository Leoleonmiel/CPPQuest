# 1. C++ / Langage et compilation  
*(C++ / Language and Compilation)*  

## 📘 Sommaire local / Local Table of Contents  
1. [1.1 Syntaxe et concepts fondamentaux / Syntax and Core Concepts](README.md#11-syntaxe-et-concepts-fondamentaux--syntax-and-core-concepts)  
2. [1.2 Classes, héritage et polymorphisme / Classes, Inheritance and Polymorphism](README.md#12-classes-héritage-et-polymorphisme--classes-inheritance-and-polymorphism)  
3. [1.3 Fonctions, templates et métaprogrammation / Functions, Templates and Metaprogramming](README.md#13-fonctions-templates-et-métaprogrammation--functions-templates-and-metaprogramming)  
4. [1.4 Mémoire et gestion des ressources / Memory and Resource Management](README.md#14-mémoire-et-gestion-des-ressources--memory-and-resource-management)  
5. [1.5 Exceptions et gestion d’erreurs / Exceptions and Error Handling](README.md#15-exceptions-et-gestion-derreurs--exceptions-and-error-handling)  
6. [1.6 Concurrence et parallélisme / Concurrency and Parallelism](README.md#16-concurrence-et-parallélisme--concurrency-and-parallelism)  
7. [1.7 C++ moderne et modules / Modern C++ and Modules](README.md#17-c-moderne-et-modules--modern-c-and-modules)  

---

## 1.1 Syntaxe et concepts fondamentaux / Syntax and Core Concepts  

1.1.1 – Qu’est-ce qu’un langage compilé et en quoi C++ diffère-t-il d’un langage interprété ?  
1.1.2 – Qu’est-ce qu’un type fondamental en C++ ?  
1.1.3 – Quelle est la différence entre une déclaration et une définition ?  
1.1.4 – Qu’est-ce qu’une conversion implicite ?  
1.1.5 – Que signifie le mot-clé `auto` ?  
1.1.6 – Quelle est la différence entre `typedef` et `using` ?  
1.1.7 – Que fait le mot-clé `namespace` ?  
1.1.8 – Quelle est la différence entre `using namespace` et une directive `using` spécifique ?  
1.1.9 – Qu’est-ce qu’un fichier header (.h) et un fichier source (.cpp) ?  
1.1.10 – Pourquoi faut-il éviter les inclusions circulaires ?  
1.1.11 – Que fait le préprocesseur avant la compilation ?  
1.1.12 – Quelle est la différence entre `#include` et `#define` ?  
1.1.13 – Qu’est-ce qu’une macro et pourquoi les éviter en C++ moderne ?  
1.1.14 – Quelle est la différence entre `inline` et `constexpr` pour une fonction ?  
1.1.15 – Qu’est-ce qu’une constante symbolique ?  
1.1.16 – Quelle est la différence entre `const` et `constexpr` ?  
1.1.17 – Que signifie `consteval` et quand l’utiliser ?  
1.1.18 – Que fait `constinit` ?  
1.1.19 – Quelle est la différence entre `mutable` et `const` ?  
1.1.20 – À quoi sert le mot-clé `volatile` ?  

---

## 1.2 Classes, héritage et polymorphisme / Classes, Inheritance and Polymorphism  

1.2.1 – Quelle est la différence entre `class` et `struct` ?  
1.2.2 – Quelle est la visibilité par défaut d’une `class` ?  
1.2.3 – Quelle est la différence entre `public`, `protected` et `private` ?  
1.2.4 – Qu’est-ce qu’un constructeur ?  
1.2.5 – Qu’est-ce qu’un destructeur et quand est-il appelé ?  
1.2.6 – Quelle est la différence entre constructeur de copie et de déplacement ?  
1.2.7 – Qu’est-ce qu’un membre statique ?  
1.2.8 – Que signifie `explicit` sur un constructeur ?  
1.2.9 – Qu’est-ce qu’un destructeur virtuel et pourquoi est-il important ?  
1.2.10 – Quelle est la différence entre redéfinition et masquage de fonction ?  
1.2.11 – Qu’est-ce que la liaison dynamique (dynamic binding) ?  
1.2.12 – Qu’est-ce qu’une fonction virtuelle pure ?  
1.2.13 – Que fait le mot-clé `override` ?  
1.2.14 – Que fait le mot-clé `final` ?  
1.2.15 – Qu’est-ce que la vtable et combien d’espace occupe-t-elle ?  
1.2.16 – Quelle est la différence entre héritage simple et multiple ?  
1.2.17 – Qu’est-ce qu’un diamant d’héritage ?  
1.2.18 – Qu’est-ce que l’héritage virtuel ?  
1.2.19 – Quelle est la différence entre composition et héritage ?  
1.2.20 – Pourquoi préférer la composition à l’héritage dans certains cas ?  

---

## 1.3 Fonctions, templates et métaprogrammation / Functions, Templates and Metaprogramming  

1.3.1 – Quelle est la différence entre fonction inline et lambda ?  
1.3.2 – Qu’est-ce qu’un pointeur de fonction ?  
1.3.3 – Quelle est la différence entre fonction membre et fonction libre ?  
1.3.4 – Qu’est-ce qu’une fonction template ?  
1.3.5 – Quelle est la différence entre spécialisation totale et partielle ?  
1.3.6 – Qu’est-ce que SFINAE et à quoi sert-il ?  
1.3.7 – Que sont les concepts introduits en C++20 ?  
1.3.8 – Quelle est la différence entre `requires` et `concept` ?  
1.3.9 – Qu’est-ce que l’instanciation d’un template ?  
1.3.10 – Pourquoi les définitions de templates doivent-elles être dans les en-têtes ?  
1.3.11 – Qu’est-ce que `decltype` et `decltype(auto)` ?  
1.3.12 – Qu’est-ce que `constexpr if` et comment il fonctionne ?  
1.3.13 – Quelle est la différence entre `typename` et `class` dans un template ?  
1.3.14 – Qu’est-ce que la déduction de type (CTAD) ?  
1.3.15 – Qu’est-ce que `std::enable_if` ?  
1.3.16 – Qu’est-ce que la métaprogrammation à la compilation ?  
1.3.17 – Quelle est la différence entre métaprogrammation et exécution ?  
1.3.18 – Qu’est-ce que `std::conditional` et `std::is_same` ?  
1.3.19 – Qu’est-ce que `concept std::integral` ?  
1.3.20 – Quelle est la différence entre SFINAE et concepts ?  

---

## 1.4 Mémoire et gestion des ressources / Memory and Resource Management  

1.4.1 – Qu’est-ce que RAII (Resource Acquisition Is Initialization) ?  
1.4.2 – Quelle est la différence entre `new/delete` et `malloc/free` ?  
1.4.3 – Qu’est-ce qu’un pointeur intelligent (`std::unique_ptr`, `std::shared_ptr`, `std::weak_ptr`) ?  
1.4.4 – Quelle est la différence entre `unique_ptr` et `shared_ptr` ?  
1.4.5 – Que fait le compteur de référence d’un `std::shared_ptr` ?  
1.4.6 – Qu’est-ce qu’une fuite mémoire et comment la détecter ?  
1.4.7 – Quelle est la différence entre allocation statique et dynamique ?  
1.4.8 – Quelle est la différence entre pile (stack) et tas (heap) ?  
1.4.9 – Qu’est-ce que la fragmentation mémoire ?  
1.4.10 – Qu’est-ce qu’un pool d’allocations ?  
1.4.11 – Qu’est-ce que l’alignement mémoire ?  
1.4.12 – Que fait l’attribut `alignas` ?  
1.4.13 – Quelle est la différence entre `placement new` et `new` normal ?  
1.4.14 – Quelle est la différence entre un pointeur brut et un pointeur géré ?  
1.4.15 – Qu’est-ce qu’un “dangling pointer” ?  
1.4.16 – Qu’est-ce qu’un `std::array` comparé à un `std::vector` ?  
1.4.17 – Quelle est la différence entre un conteneur séquentiel et associatif ?  
1.4.18 – Qu’est-ce qu’un allocateur personnalisé (`std::allocator`) ?  
1.4.19 – Qu’est-ce que la règle des trois / cinq ?  
1.4.20 – Qu’est-ce que la sémantique de mouvement ?  

---

## 1.5 Exceptions et gestion d’erreurs / Exceptions and Error Handling  

1.5.1 – Qu’est-ce qu’une exception en C++ ?  
1.5.2 – Quelle est la différence entre `throw` et `noexcept` ?  
1.5.3 – Qu’est-ce que la propagation d’une exception ?  
1.5.4 – Qu’est-ce qu’un `try` / `catch` imbriqué ?  
1.5.5 – Que fait `std::terminate` ?  
1.5.6 – Quelle est la différence entre exception standard et personnalisée ?  
1.5.7 – Qu’est-ce que `std::bad_alloc` ?  
1.5.8 – Qu’est-ce qu’un `catch(...)` ?  
1.5.9 – Quelle est la différence entre gestion d’erreur par code retour et par exception ?  
1.5.10 – Que fait `noexcept(true)` sur une fonction ?  

---

## 1.6 Concurrence et parallélisme / Concurrency and Parallelism  

1.6.1 – Qu’est-ce qu’un thread ?  
1.6.2 – Quelle est la différence entre processus et thread ?  
1.6.3 – Qu’est-ce que `std::thread` ?  
1.6.4 – Qu’est-ce qu’un `mutex` ?  
1.6.5 – Quelle est la différence entre `std::mutex` et `std::shared_mutex` ?  
1.6.6 – Qu’est-ce qu’une condition variable ?  
1.6.7 – Qu’est-ce qu’un `atomic` et pourquoi l’utiliser ?  
1.6.8 – Qu’est-ce qu’un “data race” ?  
1.6.9 – Qu’est-ce qu’un `std::future` et un `std::promise` ?  
1.6.10 – Qu’est-ce qu’un “thread pool” ?  
1.6.11 – Qu’est-ce qu’un “scheduler” ?  
1.6.12 – Qu’est-ce que `memory_order_relaxed` ?  
1.6.13 – Quelle est la différence entre exécution parallèle et concurrente ?  
1.6.14 – Qu’est-ce qu’un “deadlock” ?  
1.6.15 – Qu’est-ce que `std::async` ?  
1.6.16 – Qu’est-ce qu’un “spinlock” ?  
1.6.17 – Quelle est la différence entre “lock-free” et “wait-free” ?  
1.6.18 – Qu’est-ce que le “false sharing” ?  
1.6.19 – Qu’est-ce que la synchronisation de threads ?  
1.6.20 – Qu’est-ce que `std::barrier` ?  

---

## 1.7 C++ moderne et modules / Modern C++ and Modules  

1.7.1 – Qu’est-ce qu’un module en C++20 ?  
1.7.2 – Quelle est la différence entre module et header classique ?  
1.7.3 – Qu’est-ce qu’un “interface partition” ?  
1.7.4 – Qu’est-ce que la directive `export` ?  
1.7.5 – Qu’est-ce que `import std;` ?  
1.7.6 – Quelle est la différence entre “header units” et modules ?  
1.7.7 – Qu’est-ce que `std::ranges` ?  
1.7.8 – Qu’est-ce qu’un “concept constraint” ?  
1.7.9 – Quelle est la différence entre “structured bindings” et tuples ?  
1.7.10 – Qu’est-ce que `std::span` ?  
