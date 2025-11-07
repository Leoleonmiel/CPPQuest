# 15. Design Patterns et architecture logicielle  
*(Software Design Patterns and Architecture)*  

---

## 15.1 Patterns de création / Creational Patterns  

### 15.1.1  
Qu’est-ce qu’un *Singleton* et quels en sont les inconvénients ?  
```cpp
class Singleton {
private:
    Singleton() = default;
public:
    static Singleton& instance() {
        static Singleton s;
        return s;
    }
};
```
---

### 15.1.2  
Comment implémenter un *Factory Method* pour créer différents types d’objets sans connaître leurs classes concrètes ?  
```cpp
class Shape { public: virtual void draw() = 0; };
class Circle : public Shape { public: void draw() override {} };
class Square : public Shape { public: void draw() override {} };

class ShapeFactory {
public:
    static Shape* Create(const std::string& type);
};
```
---

### 15.1.3  
Expliquez la différence entre *Factory Method* et *Abstract Factory*.  

---

### 15.1.4  
Comment garantir la *thread-safety* d’un Singleton dans un environnement multithread ?  

---

### 15.1.5  
Quel est le rôle du *Builder Pattern* et quand le préférer à un constructeur complexe ?  
```cpp
class Car {
    std::string model;
    int wheels;
public:
    class Builder {
        Car c;
    public:
        Builder& model(const std::string& m) { c.model = m; return *this; }
        Builder& wheels(int n) { c.wheels = n; return *this; }
        Car build() { return c; }
    };
};
```
---

### 15.1.6  
Que permet le *Prototype Pattern* et comment l’implémenter efficacement en C++ ?  
```cpp
class Prototype {
public:
    virtual Prototype* clone() const = 0;
};
```
---

## 15.2 Patterns structurels / Structural Patterns  

### 15.2.1  
Quelle est la différence entre *Adapter* et *Bridge Pattern* ?  

---

### 15.2.2  
Implémentez un *Adapter* pour rendre compatible deux interfaces.  
```cpp
class LegacyPrinter {
public:
    void printOld(const std::string& s) {}
};

class ModernPrinter {
public:
    void print(const std::string& s) {}
};

class Adapter : public ModernPrinter {
    LegacyPrinter* legacy;
public:
    Adapter(LegacyPrinter* l) : legacy(l) {}
    void print(const std::string& s) { legacy->printOld(s); }
};
```
---

### 15.2.3  
Comment le *Composite Pattern* permet-il de traiter objets simples et composites de manière uniforme ?  

---

### 15.2.4  
Quelle est la différence entre *Proxy* et *Decorator* ?  

---

### 15.2.5  
Donnez un exemple de *Decorator* appliqué à un flux.  
```cpp
class Stream {
public:
    virtual void write(const std::string&) = 0;
};

class FileStream : public Stream {
public:
    void write(const std::string& s) override {}
};

class BufferedStream : public Stream {
    Stream* inner;
public:
    BufferedStream(Stream* s) : inner(s) {}
    void write(const std::string& s) override { inner->write(s); }
};
```
---

### 15.2.6  
Expliquez comment le *Flyweight Pattern* optimise la mémoire.  

---

## 15.3 Patterns comportementaux / Behavioral Patterns  

### 15.3.1  
Décrivez le *Observer Pattern* et son implémentation typique.  
```cpp
class Observer {
public:
    virtual void onNotify(int event) = 0;
};

class Subject {
    std::vector<Observer*> obs;
public:
    void attach(Observer* o) { obs.push_back(o); }
    void notify(int e) { for (auto* o : obs) o->onNotify(e); }
};
```
---

### 15.3.2  
Quelle est la différence entre *Observer* et *Mediator* ?  

---

### 15.3.3  
Implémentez un *Command Pattern*.  
```cpp
class Command {
public:
    virtual void execute() = 0;
};

class LightOn : public Command {
public:
    void execute() override { /* turn on light */ }
};

class Invoker {
    Command* cmd;
public:
    void set(Command* c) { cmd = c; }
    void run() { cmd->execute(); }
};
```
---

### 15.3.4  
À quoi sert le *State Pattern* et comment évite-t-il les `switch` géants ?  

---

### 15.3.5  
Comment fonctionne le *Strategy Pattern* en C++ moderne ?  
```cpp
class SortStrategy {
public:
    virtual void sort(std::vector<int>&) = 0;
};

class QuickSort : public SortStrategy {
public:
    void sort(std::vector<int>& v) override { /* ... */ }
};

class Context {
    SortStrategy* s;
public:
    Context(SortStrategy* s) : s(s) {}
    void doSort(std::vector<int>& v) { s->sort(v); }
};
```
---

### 15.3.6  
Expliquez le *Visitor Pattern* et ses usages en parsing.  

---

## 15.4 Patterns modernes C++ / Modern C++ Patterns  

### 15.4.1  
Comment implémenter un *RAII Pattern* générique avec `unique_ptr` ?  

---

### 15.4.2  
Quel est le rôle du *PImpl (Pointer to Implementation)* ?  
```cpp
class Widget {
    struct Impl;
    std::unique_ptr<Impl> pImpl;
public:
    Widget();
    ~Widget();
};
```
---

### 15.4.3  
Comment utiliser les *Concepts* pour exprimer un pattern de stratégie générique ?  
```cpp
template<typename T>
concept Sorter = requires(T t, std::vector<int>& v) { t.sort(v); };

void sortWith(Sorter auto s, std::vector<int>& v) { s.sort(v); }
```
---

### 15.4.4  
Expliquez le *Dependency Injection Pattern* appliqué à C++.  

---

### 15.4.5  
Comment appliquer le *CRTP (Curiously Recurring Template Pattern)* ?  
```cpp
template<class Derived>
class Base {
public:
    void interface() { static_cast<Derived*>(this)->impl(); }
};

class Derived : public Base<Derived> {
public:
    void impl() {}
};
```
---

### 15.4.6  
Comment combiner *RAII* et *ScopeGuard* pour la sécurité d’exécution ?  
```cpp
class ScopeGuard {
    std::function<void()> f;
public:
    ScopeGuard(std::function<void()> func) : f(func) {}
    ~ScopeGuard() { f(); }
};
```
---

## 15.5 Patterns de concurrence / Concurrency Patterns  

### 15.5.1  
Décrivez le *Thread Pool Pattern* et sa mise en œuvre de base.  
```cpp
class ThreadPool {
    std::vector<std::thread> threads;
    std::queue<std::function<void()>> tasks;
    std::mutex m;
    std::condition_variable cv;
    bool stop = false;
public:
    ThreadPool(size_t n);
    void enqueue(std::function<void()> f);
    ~ThreadPool();
};
```
---

### 15.5.2  
Comment le *Producer–Consumer Pattern* peut-il être implémenté efficacement ?  

---

### 15.5.3  
Expliquez le *Active Object Pattern*.  

---

### 15.5.4  
Quelle est la différence entre *Future/Promise* et *Task-based concurrency* ?  

---

### 15.5.5  
Comment garantir la *thread-safety* d’un *Singleton concurrent* ?  

---

### 15.5.6  
Donnez un exemple d’utilisation du *Monitor Pattern*.  

---

## 15.6 Architecture logicielle et principes SOLID / Software Architecture and SOLID Principles  

### 15.6.1  
Décrivez brièvement les cinq principes SOLID.  

---

### 15.6.2  
Comment le *Dependency Inversion Principle* favorise-t-il la testabilité ?  

---

### 15.6.3  
Quelle est la différence entre *Layered* et *Hexagonal Architecture* ?  

---

### 15.6.4  
Expliquez le concept d’*Event-driven architecture* et ses avantages.  

---

### 15.6.5  
Comment appliquer le *Model–View–ViewModel (MVVM)* en C++ ?  

---

### 15.6.6  
Quelle est la relation entre *Entity Component System (ECS)* et *Composition over Inheritance* ?  

---

