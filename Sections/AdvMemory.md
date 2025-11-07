# 18. Gestion mémoire avancée et patterns d’allocation  
*(Advanced Memory Management and Allocation Patterns)*  

## 18.1 Allocateurs personnalisés / Custom Allocators  

18.1.1 — Qu’est-ce qu’un allocateur personnalisé en C++ et à quoi sert-il ?  
18.1.2 — Comment les allocateurs s’intègrent-ils avec la STL ?  
18.1.3 — Quelle différence existe-t-il entre `std::allocator` et un allocateur sur mesure ?  
18.1.4 — Dans quel cas implémenter un allocateur mémoire spécifique à un conteneur ?  
18.1.5 — Comment un allocateur gère-t-il la construction et la destruction des objets ?  
18.1.6 — Pourquoi utiliser un allocateur stateless plutôt que stateful ?  
18.1.7 — Quelles sont les contraintes de thread-safety d’un allocateur ?  
18.1.8 — Comment minimiser la fragmentation mémoire dans un allocateur ?  
18.1.9 — Qu’est-ce que la réutilisation de blocs (“block reuse”) ?  
18.1.10 — Comment mesurer la performance d’un allocateur personnalisé ?  

---

## 18.2 Pool allocators et slabs / Pool and Slab Allocators  

18.2.1 — Qu’est-ce qu’un pool allocator et quand est-il utile ?  
18.2.2 — Quelle est la différence entre un pool allocator et un slab allocator ?  
18.2.3 — Pourquoi les moteurs 3D et jeux utilisent-ils des pool allocators ?  
18.2.4 — Comment un pool allocator améliore-t-il la localité mémoire ?  
18.2.5 — Qu’est-ce qu’un “free list” et comment est-il utilisé dans un pool allocator ?  
18.2.6 — Quelle est la complexité temporelle typique d’une allocation dans un pool ?  
18.2.7 — Quelles stratégies permettent d’éviter la fragmentation interne ?  
18.2.8 — Comment réinitialiser un pool allocator efficacement ?  
18.2.9 — Quelles sont les limites principales d’un pool allocator ?  
18.2.10 — Quelles différences entre un pool fixe et un pool extensible ?  

---

## 18.3 Arena allocators et regroupement mémoire / Arena Allocators and Memory Grouping  

18.3.1 — Qu’est-ce qu’un arena allocator ?  
18.3.2 — Quelle est la différence entre un arena allocator et un heap classique ?  
18.3.3 — Pourquoi les compilateurs utilisent-ils des arenas ?  
18.3.4 — Qu’est-ce que la réinitialisation en masse (“bulk reset”) d’une arena ?  
18.3.5 — Comment éviter les fuites de mémoire dans une arena ?  
18.3.6 — Qu’est-ce que le “linear allocation model” ?  
18.3.7 — Quels types d’applications tirent parti d’un modèle en arène ?  
18.3.8 — Comment implémenter un “stack allocator” à partir d’une arena ?  
18.3.9 — Quelle est la relation entre une arena et un contexte mémoire ?  
18.3.10 — Comment combiner un arena allocator avec des pools ?  

---

## 18.4 Cache locality et alignment / Cache Locality and Alignment  

18.4.1 — Qu’est-ce que la localité spatiale et temporelle en mémoire ?  
18.4.2 — Comment un allocateur peut-il améliorer la localité de cache ?  
18.4.3 — Qu’est-ce que le false sharing et comment l’éviter ?  
18.4.4 — Quelle est la taille typique d’une ligne de cache moderne ?  
18.4.5 — Qu’est-ce que l’alignement mémoire et pourquoi est-ce important ?  
18.4.6 — Quelle est la différence entre alignement naturel et explicite ?  
18.4.7 — Comment aligner dynamiquement une allocation sur 32 ou 64 octets ?  
18.4.8 — Comment les structures de données “SoA” (Structure of Arrays) améliorent-elles le cache ?  
18.4.9 — Qu’est-ce qu’un prefetch manuel et comment l’utiliser correctement ?  
18.4.10 — Quelle est la différence entre localité de données et localité d’instructions ?  

---

## 18.5 Paging CPU/GPU et mapping mémoire / CPU-GPU Paging and Memory Mapping  

18.5.1 — Qu’est-ce que la pagination (paging) mémoire ?  
18.5.2 — Quelle est la taille typique d’une page mémoire (x86-64, ARM) ?  
18.5.3 — Qu’est-ce qu’un TLB (Translation Lookaside Buffer) ?  
18.5.4 — Qu’est-ce qu’un page fault et comment le gérer ?  
18.5.5 — Quelle différence entre virtual et physical memory mapping ?  
18.5.6 — Comment un GPU mappe la mémoire CPU via PCIe ?  
18.5.7 — Qu’est-ce que la mémoire unifiée CUDA (“Unified Memory”) ?  
18.5.8 — Qu’est-ce que le “zero-copy mapping” sur GPU ?  
18.5.9 — Comment fonctionne le “GPU paging” dans DirectX 12 ?  
18.5.10 — Qu’est-ce qu’un “BAR region” dans un GPU ?  

---

## 18.6 Gestion mémoire haute performance / High-Performance Memory Management  

18.6.1 — Quelles sont les limites de `new` et `delete` standards ?  
18.6.2 — Qu’est-ce que `std::pmr::memory_resource` ?  
18.6.3 — Quelle est la différence entre `new` global et placement new ?  
18.6.4 — Comment le pattern “object pool” améliore-t-il les performances ?  
18.6.5 — Quelle est la différence entre `malloc` et `operator new` ?  
18.6.6 — Comment les conteneurs STL peuvent-ils tirer parti des allocateurs PMR ?  
18.6.7 — Qu’est-ce que la mémoire NUMA et pourquoi l’optimiser ?  
18.6.8 — Comment profiler l’utilisation mémoire sur CPU et GPU ?  
18.6.9 — Qu’est-ce que la fragmentation externe et comment la réduire ?  
18.6.10 — Quelles métriques suivre pour optimiser la gestion mémoire dans un moteur 3D ?  

---

## 18.7 Techniques d’allocation dans les moteurs 3D / Allocation Techniques in 3D Engines  

18.7.1 — Pourquoi les moteurs de jeu utilisent-ils des allocateurs spécialisés ?  
18.7.2 — Quelle est la différence entre une allocation frame-based et permanente ?  
18.7.3 — Qu’est-ce qu’un “frame allocator” et pourquoi est-il réinitialisé chaque frame ?  
18.7.4 — Comment gérer la mémoire pour des milliers d’objets de courte durée de vie ?  
18.7.5 — Qu’est-ce que le streaming mémoire dans un moteur de rendu ?  
18.7.6 — Comment un moteur gère-t-il la mémoire GPU pour les textures et meshes ?  
18.7.7 — Qu’est-ce que le “bindless resource management” ?  
18.7.8 — Comment structurer un allocator global multi-threadé pour le moteur ?  
18.7.9 — Qu’est-ce qu’une stratégie de “double buffering” en mémoire ?  
18.7.10 — Quelles sont les meilleures pratiques d’allocation pour un moteur de jeu temps réel ?  

---
