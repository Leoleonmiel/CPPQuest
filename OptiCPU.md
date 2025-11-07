# 4. Calcul numérique et optimisation CPU / GPU  
*(Numerical Computation and CPU / GPU Optimization)*  

## 📘 Sommaire local / Local Table of Contents  
1. [4.1 Calcul et représentation numérique / Numeric Computation and Representation](#41-calcul-et-représentation-numérique--numeric-computation-and-representation)  
2. [4.2 Optimisation CPU et SIMD / CPU Optimization and SIMD](#42-optimisation-cpu-et-simd--cpu-optimization-and-simd)  
3. [4.3 Calcul parallèle GPU et SIMT / GPU Parallel Computation and SIMT](#43-calcul-parallèle-gpu-et-simt--gpu-parallel-computation-and-simt)  
4. [4.4 Performance et mémoire / Performance and Memory Management](#44-performance-et-mémoire--performance-and-memory-management)  

---

## 4.1 Calcul et représentation numérique / Numeric Computation and Representation  

4.1.1 – Quelle est la différence entre entier, flottant et double précision ?  
4.1.2 – Qu’est-ce qu’un flottant IEEE 754 ?  
4.1.3 – Quelle est la différence entre mantisse et exposant ?  
4.1.4 – Qu’est-ce que la précision relative d’un float 32 bits ?  
4.1.5 – Qu’est-ce qu’un overflow numérique ?  
4.1.6 – Qu’est-ce qu’un underflow ?  
4.1.7 – Qu’est-ce que la stabilité numérique ?  
4.1.8 – Quelle est la différence entre erreur absolue et relative ?  
4.1.9 – Qu’est-ce qu’une erreur d’arrondi ?  
4.1.10 – Qu’est-ce qu’un epsilon machine ?  
4.1.11 – Pourquoi l’ordre des opérations influence le résultat flottant ?  
4.1.12 – Quelle est la différence entre précision simple et double dans les shaders ?  
4.1.13 – Qu’est-ce qu’une opération FMA (Fused Multiply-Add) ?  
4.1.14 – Qu’est-ce qu’un type half-float (FP16) ?  
4.1.15 – Pourquoi utiliser des flottants 16 bits sur GPU ?  
4.1.16 – Qu’est-ce que la quantification numérique ?  
4.1.17 – Quelle est la différence entre normalisation et quantification ?  
4.1.18 – Qu’est-ce qu’un overflow d’entier signé ?  
4.1.19 – Pourquoi éviter les divisions dans les shaders ?  
4.1.20 – Quelle est la différence entre calcul exact et approché ?  

---

## 4.2 Optimisation CPU et SIMD / CPU Optimization and SIMD  

4.2.1 – Qu’est-ce que SIMD (Single Instruction Multiple Data) ?  
4.2.2 – Quelle est la différence entre SIMD et MIMD ?  
4.2.3 – Qu’est-ce qu’un registre vectoriel ?  
4.2.4 – Quelle est la différence entre SSE, AVX et AVX-512 ?  
4.2.5 – Qu’est-ce qu’un pipeline d’exécution CPU ?  
4.2.6 – Quelle est la différence entre superscalaire et vectoriel ?  
4.2.7 – Qu’est-ce qu’un “cache miss” ?  
4.2.8 – Qu’est-ce qu’un cache line ?  
4.2.9 – Qu’est-ce que le “false sharing” ?  
4.2.10 – Quelle est la différence entre L1, L2, L3 cache ?  
4.2.11 – Qu’est-ce qu’une opération alignée en mémoire ?  
4.2.12 – Quelle est la différence entre “load aligned” et “load unaligned” ?  
4.2.13 – Qu’est-ce qu’une optimisation de boucle (loop unrolling) ?  
4.2.14 – Qu’est-ce que le “branch prediction” ?  
4.2.15 – Qu’est-ce qu’une dépendance de données ?  
4.2.16 – Quelle est la différence entre parallélisme d’instruction et de données ?  
4.2.17 – Qu’est-ce que l’inlining manuel ?  
4.2.18 – Qu’est-ce que la vectorisation automatique ?  
4.2.19 – Quelle est la différence entre compilation avec `-O1`, `-O2`, `-O3` ?  
4.2.20 – Pourquoi profiler un programme avant de l’optimiser ?  

---

## 4.3 Calcul parallèle GPU et SIMT / GPU Parallel Computation and SIMT  

4.3.1 – Qu’est-ce que SIMT (Single Instruction Multiple Threads) ?  
4.3.2 – Quelle est la différence entre SIMD et SIMT ?  
4.3.3 – Quelle est la structure d’un GPU moderne ?  
4.3.4 – Qu’est-ce qu’un multiprocesseur de flux (SM) ?  
4.3.5 – Qu’est-ce qu’un warp ou wavefront ?  
4.3.6 – Qu’est-ce qu’une divergence de thread ?  
4.3.7 – Qu’est-ce qu’un bloc et une grille CUDA ?  
4.3.8 – Quelle est la différence entre mémoire globale, partagée et constante ?  
4.3.9 – Qu’est-ce que la mémoire coalescée ?  
4.3.10 – Pourquoi l’accès mémoire coalescé est-il plus rapide ?  
4.3.11 – Qu’est-ce qu’un kernel GPU ?  
4.3.12 – Quelle est la différence entre CUDA et OpenCL ?  
4.3.13 – Qu’est-ce qu’un “compute shader” ?  
4.3.14 – Quelle est la différence entre shader de calcul et vertex shader ?  
4.3.15 – Qu’est-ce que la synchronisation de threads GPU ?  
4.3.16 – Qu’est-ce qu’un “barrier” GPU ?  
4.3.17 – Qu’est-ce que la local work size dans OpenCL ?  
4.3.18 – Quelle est la différence entre GPU intégré et dédié ?  
4.3.19 – Qu’est-ce qu’une réduction parallèle (parallel reduction) ?  
4.3.20 – Qu’est-ce qu’un algorithme “embarrassingly parallel” ?  

---

## 4.4 Performance et mémoire / Performance and Memory Management  

4.4.1 – Qu’est-ce qu’un goulot d’étranglement mémoire (memory bottleneck) ?  
4.4.2 – Quelle est la différence entre latence et bande passante ?  
4.4.3 – Qu’est-ce que le “cache locality” ?  
4.4.4 – Quelle est la différence entre accès séquentiel et aléatoire ?  
4.4.5 – Qu’est-ce qu’une politique de préchargement (prefetch) ?  
4.4.6 – Qu’est-ce qu’une “memory pool” pour GPU ?  
4.4.7 – Quelle est la différence entre mémoire partagée et unifiée sur GPU ?  
4.4.8 – Qu’est-ce que la mémoire paginée ?  
4.4.9 – Quelle est la différence entre mémoire pinned et pageable ?  
4.4.10 – Qu’est-ce qu’un “memory fence” ?  
4.4.11 – Pourquoi aligner les données sur 16 ou 32 octets ?  
4.4.12 – Quelle est la différence entre structure of arrays (SoA) et array of structures (AoS) ?  
4.4.13 – Pourquoi SoA est plus efficace pour SIMD/SIMT ?  
4.4.14 – Qu’est-ce que la cohérence de cache entre CPU et GPU ?  
4.4.15 – Quelle est la différence entre transfert synchrone et asynchrone ?  
4.4.16 – Qu’est-ce qu’un “pipeline de calcul” sur GPU ?  
4.4.17 – Pourquoi découper un calcul en batchs peut améliorer la performance ?  
4.4.18 – Qu’est-ce qu’un “compute bound” vs “memory bound” kernel ?  
4.4.19 – Quelle est la différence entre “profiling” et “benchmarking” ?  
4.4.20 – Qu’est-ce qu’un outil de profilage GPU (Nsight, Radeon GPU Profiler, etc.) ?  
