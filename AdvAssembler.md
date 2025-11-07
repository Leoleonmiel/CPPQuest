# 11. Assembleur avancé et optimisation bas-niveau  
*(Advanced Assembly and Low-Level Optimization)*  

## 📘 Sommaire local / Local Table of Contents  
1. [11.1 Instructions complexes et micro-opérations / Complex Instructions and Micro-operations](#111-instructions-complexes-et-micro-opérations--complex-instructions-and-micro-operations)  
2. [11.2 Inline assembly et intégration C++ / Inline Assembly and C++ Integration](#112-inline-assembly-et-intégration-c--inline-assembly-and-c-integration)  
3. [11.3 ABI, conventions d’appel et linkage / ABI, Calling Conventions and Linkage](#113-abi-conventions-dappel-et-linkage--abi-calling-conventions-and-linkage)  
4. [11.4 Profilage et débogage bas-niveau / Low-Level Profiling and Debugging](#114-profilage-et-débogage-bas-niveau--low-level-profiling-and-debugging)  
5. [11.5 Reverse engineering et désassemblage / Reverse Engineering and Disassembly](#115-reverse-engineering-et-désassemblage--reverse-engineering-and-disassembly)  
6. [11.6 Optimisation spécifique architecture / Architecture-Specific Optimization](#116-optimisation-spécifique-architecture--architecture-specific-optimization)  

---

## 11.1 Instructions complexes et micro-opérations / Complex Instructions and Micro-operations  

11.1.1 – Qu’est-ce qu’une instruction micro-codée ?  
11.1.2 – Quelle est la différence entre CISC et RISC ?  
11.1.3 – Qu’est-ce qu’une micro-opération (µop) dans le pipeline ?  
11.1.4 – Qu’est-ce que le “macro-fusion” et “micro-fusion” ?  
11.1.5 – Qu’est-ce qu’une instruction multi-cycle ?  
11.1.6 – Quelle est la différence entre “latency” et “throughput” ?  
11.1.7 – Qu’est-ce qu’un “port scheduler” dans un CPU moderne ?  
11.1.8 – Qu’est-ce que le “loop buffer” ?  
11.1.9 – Qu’est-ce qu’un micro-op cache ?  
11.1.10 – Quelle est la différence entre décodage simple et complexe ?  

---

## 11.2 Inline assembly et intégration C++ / Inline Assembly and C++ Integration  

11.2.1 – Qu’est-ce que l’assembleur inline (`asm` ou `__asm__`) ?  
11.2.2 – Comment insérer une instruction assembleur dans une fonction C++ ?  
11.2.3 – Quelle est la différence entre syntaxe Intel et AT&T ?  
11.2.4 – Qu’est-ce que la contrainte `"r"`, `"m"`, `"a"` dans GCC inline asm ?  
11.2.5 – Qu’est-ce que le mot-clé `volatile` en assembleur inline ?  
11.2.6 – Quelles sont les différences entre GCC et MSVC pour l’inline assembly ?  
11.2.7 – Qu’est-ce que la contrainte `"memory"` ?  
11.2.8 – Comment éviter la destruction d’un registre dans un bloc `asm` ?  
11.2.9 – Qu’est-ce qu’un “clobber list” ?  
11.2.10 – Comment utiliser les intrinsics au lieu de l’assembleur pur ?  

---

## 11.3 ABI, conventions d’appel et linkage / ABI, Calling Conventions and Linkage  

11.3.1 – Qu’est-ce que l’ABI (Application Binary Interface) ?  
11.3.2 – Quelle est la différence entre ABI et API ?  
11.3.3 – Quelles sont les conventions d’appel sous x86_64 ?  
11.3.4 – Quelles différences entre System V AMD64 et Microsoft x64 ?  
11.3.5 – Quels registres servent à passer les arguments ?  
11.3.6 – Qu’est-ce qu’un alignement de pile ?  
11.3.7 – Qu’est-ce que le “shadow space” Windows ?  
11.3.8 – Comment sont gérés les retours de structure par valeur ?  
11.3.9 – Qu’est-ce que la convention `fastcall` sur x86 ?  
11.3.10 – Quelle est la différence entre linkage C et C++ (`extern "C"`) ?  

---

## 11.4 Profilage et débogage bas-niveau / Low-Level Profiling and Debugging  

11.4.1 – Qu’est-ce qu’un breakpoint matériel ?  
11.4.2 – Quelle est la différence entre `int3` et `breakpoint hardware` ?  
11.4.3 – Qu’est-ce que le registre `DR0–DR7` ?  
11.4.4 – Qu’est-ce que le mode “single step” (`TF` flag) ?  
11.4.5 – Qu’est-ce que les compteurs de performance (PMC) ?  
11.4.6 – Qu’est-ce qu’une mesure de “cycles” via `rdtsc` ?  
11.4.7 – Qu’est-ce que le “branch trace store” ?  
11.4.8 – Quelle est la différence entre profilage échantillonné et instrumenté ?  
11.4.9 – Qu’est-ce que la trace ETW (Windows) ou Perf (Linux) ?  
11.4.10 – Qu’est-ce qu’un crash dump et comment l’analyser ?  

---

## 11.5 Reverse engineering et désassemblage / Reverse Engineering and Disassembly  

11.5.1 – Quelle est la différence entre désassemblage statique et dynamique ?  
11.5.2 – Qu’est-ce que la signature d’une fonction en binaire ?  
11.5.3 – Qu’est-ce qu’un outil de désassemblage (IDA, Ghidra, Radare2) ?  
11.5.4 – Qu’est-ce que la détection de pattern d’instruction ?  
11.5.5 – Qu’est-ce qu’une fonction inline dans le binaire ?  
11.5.6 – Qu’est-ce qu’un “symbol stripping” ?  
11.5.7 – Qu’est-ce que l’optimisation de compilateur difficile à inverser ?  
11.5.8 – Qu’est-ce que la reconstruction de flot de contrôle ?  
11.5.9 – Qu’est-ce que la désobfuscation de code machine ?  
11.5.10 – Qu’est-ce qu’un “packed binary” ?  

---

## 11.6 Optimisation spécifique architecture / Architecture-Specific Optimization  

11.6.1 – Qu’est-ce que le “cache prefetching” ?  
11.6.2 – Qu’est-ce qu’une latence mémoire L1/L2/L3 ?  
11.6.3 – Qu’est-ce que l’alignement de données 16 octets ?  
11.6.4 – Qu’est-ce que le “branch target buffer” ?  
11.6.5 – Qu’est-ce que la micro-op fusion ?  
11.6.6 – Qu’est-ce que le port contention ?  
11.6.7 – Qu’est-ce que la technique de “loop unrolling” ?  
11.6.8 – Qu’est-ce que le “software pipelining” ?  
11.6.9 – Qu’est-ce que la vectorisation manuelle ?  
11.6.10 – Qu’est-ce que la synchronisation fine entre threads à niveau assembleur ?  
