# 12. Lecture, correction et optimisation de code  
*(Code Debugging and Optimization)*  

## 12.1 Boucles et performances  

### 12.1.1  
Réécrivez ce code pour éviter les appels inutiles et améliorer les accès mémoire.  
```cpp
uint32_t Rand32();
char buffer[4096];
for (size_t i = 0; i < 4096; i++)
{
    buffer[i] = (char)Rand32();
}
```
---

### 12.1.2  
Expliquez pourquoi ce code est lent et comment utiliser un buffer temporaire.  
```cpp
for (int i = 0; i < data.size(); ++i)
{
    data[i] += sqrt(i);
}
```
---

### 12.1.3  
Optimisez cette fonction pour réduire le nombre d’allocations dynamiques.  
```cpp
std::vector<int> Compute()
{
    std::vector<int> v;
    for (int i = 0; i < 1000000; ++i)
        v.push_back(i * 2);
    return v;
}
```
---

## 12.2 Gestion mémoire et erreurs  

### 12.2.1  
Trouvez le bug mémoire dans ce code.  
```cpp
char* Copy(const char* src)
{
    char buffer[64];
    strcpy(buffer, src);
    return buffer;
}
```
---

### 12.2.2  
Expliquez pourquoi ce code fuit de la mémoire.  
```cpp
void foo()
{
    int* p = new int[10];
    for (int i = 0; i < 10; ++i)
        p[i] = i;
}
```
---

### 12.2.3  
Corrigez ce code pour qu’il soit sûr et moderne.  
```cpp
class Data
{
public:
    Data() { m = new int[10]; }
    ~Data() {}
private:
    int* m;
};
```
---

## 12.3 Polymorphisme et héritage  

### 12.3.1  
Quel est l’output de ce programme ?  
```cpp
class A
{
public:
    virtual void Print() { printf("A\n"); }
};

class B : public A
{
public:
    void Print() { printf("B\n"); }
};

int main()
{
    A* p = new B;
    p->Print();
    ((B*)p)->Print();
}
```
---

### 12.3.2  
Que se passe-t-il si la fonction Print de B n’est pas virtuelle ?  

---

### 12.3.3  
Expliquez le rôle de la vtable et son impact sur la taille d’un objet.  

---

## 12.4 Templates et généricité  

### 12.4.1  
Rendez cette classe capable de stocker n’importe quel type.  
```cpp
class Array
{
public:
    unsigned int get(unsigned int _index)
    {
        return *(m_unsignedInts + _index);
    }
private:
    unsigned int* m_unsignedInts{ nullptr };
    unsigned int m_size{ 0 };
    unsigned int m_capacity{ 0 };
};
```
---

### 12.4.2  
Pourquoi le code suivant ne compile-t-il pas ?  
```cpp
template<typename T>
void Print(T value)
{
    if (value > 0)
        printf("%d", value);
}

int main()
{
    Print("hello");
}
```
---

### 12.4.3  
Expliquez comment résoudre le problème en utilisant `std::is_integral`.  

---

## 12.5 Multithreading et synchronisation  

### 12.5.1  
Identifiez le bug de synchronisation.  
```cpp
int counter = 0;

void ThreadFunc()
{
    for (int i = 0; i < 10000; ++i)
        counter++;
}

int main()
{
    std::thread t1(ThreadFunc);
    std::thread t2(ThreadFunc);
    t1.join();
    t2.join();
    printf("%d", counter);
}
```
---

### 12.5.2  
Expliquez comment corriger le code avec `std::mutex`.  

---

### 12.5.3  
Pourquoi la contention du verrou peut-elle dégrader les performances ?  

---

## 12.6 Calculs 3D et optimisation SIMD  

### 12.6.1  
Réécrivez la multiplication de matrice suivante pour améliorer le cache.  
```cpp
for (int i = 0; i < N; ++i)
    for (int j = 0; j < N; ++j)
        for (int k = 0; k < N; ++k)
            C[i][j] += A[i][k] * B[k][j];
```
---

### 12.6.2  
Comment vectoriser cette boucle avec AVX2 ou SSE ?  

---

### 12.6.3  
Quelle serait la meilleure disposition mémoire (row-major ou column-major) ?  

---

### 12.6.4  
Expliquez comment appliquer un alignement mémoire 32 bits sur un tableau `float`.  

---
