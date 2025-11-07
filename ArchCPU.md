# 6. Architecture CPU  
*(CPU Architecture and Microarchitecture)*  

## 📘 Sommaire local / Local Table of Contents  
1. [6.1 Structure générale d’un processeur / General Processor Structure](#61-structure-générale-dun-processeur--general-processor-structure)  
2. [6.2 Pipeline et exécution des instructions / Instruction Pipeline and Execution](#62-pipeline-et-exécution-des-instructions--instruction-pipeline-and-execution)  
3. [6.3 Mémoire cache et hiérarchie / Cache Memory and Hierarchy](#63-mémoire-cache-et-hiérarchie--cache-memory-and-hierarchy)  
4. [6.4 Parallélisme et multithreading / Parallelism and Multithreading](#64-parallélisme-et-multithreading--parallelism-and-multithreading)  
5. [6.5 Gestion des instructions et prédiction / Instruction Control and Prediction](#65-gestion-des-instructions-et-prédiction--instruction-control-and-prediction)  
6. [6.6 Communication et cohérence mémoire / Communication and Memory Coherency](#66-communication-et-cohérence-mémoire--communication-and-memory-coherency)  

---

## 6.1 Structure générale d’un processeur / General Processor Structure  

6.1.1 – Quelles sont les principales unités fonctionnelles d’un CPU ?  
6.1.2 – Qu’est-ce que l’unité de contrôle ?  
6.1.3 – Qu’est-ce qu’une unité arithmétique et logique (ALU) ?  
6.1.4 – Quelle est la différence entre ALU et FPU ?  
6.1.5 – Qu’est-ce que le registre d’instruction (IR) ?  
6.1.6 – Qu’est-ce qu’un bus de données et un bus d’adresses ?  
6.1.7 – Quelle est la différence entre architecture Harvard et Von Neumann ?  
6.1.8 – Qu’est-ce qu’un jeu d’instructions (ISA) ?  
6.1.9 – Quelle est la différence entre CISC et RISC ?  
6.1.10 – Qu’est-ce qu’une microarchitecture ?  
6.1.11 – Quelle est la différence entre architecture et microarchitecture ?  
6.1.12 – Qu’est-ce qu’un registre général (GPR) ?  
6.1.13 – Qu’est-ce qu’un registre spécial (flags, PC, SP) ?  
6.1.14 – Qu’est-ce qu’un front-end et un back-end CPU ?  
6.1.15 – Quelle est la différence entre décodage et exécution d’instruction ?  
6.1.16 – Qu’est-ce qu’un “issue width” ?  
6.1.17 – Qu’est-ce que l’horloge d’un processeur ?  
6.1.18 – Quelle est la différence entre fréquence et IPC (Instructions Per Cycle) ?  
6.1.19 – Qu’est-ce qu’un “throughput” CPU ?  
6.1.20 – Quelle est la différence entre architecture 32 bits et 64 bits ?  

---

## 6.2 Pipeline et exécution des instructions / Instruction Pipeline and Execution  

6.2.1 – Qu’est-ce qu’un pipeline d’instructions ?  
6.2.2 – Quelles sont les étapes typiques d’un pipeline (Fetch, Decode, Execute, etc.) ?  
6.2.3 – Qu’est-ce qu’un “pipeline stall” ?  
6.2.4 – Qu’est-ce qu’une dépendance de données ?  
6.2.5 – Quelle est la différence entre RAW, WAR et WAW ?  
6.2.6 – Qu’est-ce que le “pipeline hazard” ?  
6.2.7 – Qu’est-ce que la réordonnancement des instructions (out-of-order execution) ?  
6.2.8 – Qu’est-ce que le “instruction window” ?  
6.2.9 – Qu’est-ce que le “reorder buffer” ?  
6.2.10 – Qu’est-ce qu’un “reservation station” ?  
6.2.11 – Quelle est la différence entre exécution séquentielle et parallèle ?  
6.2.12 – Qu’est-ce que le “branch misprediction” ?  
6.2.13 – Qu’est-ce que la “speculative execution” ?  
6.2.14 – Quelle est la différence entre exécution spéculative et prédiction de branche ?  
6.2.15 – Qu’est-ce qu’un “instruction retire” ?  
6.2.16 – Qu’est-ce que le “superscalar pipeline” ?  
6.2.17 – Quelle est la différence entre pipeline simple et multiple ?  
6.2.18 – Qu’est-ce que la latence d’instruction ?  
6.2.19 – Quelle est la différence entre débit et latence ?  
6.2.20 – Qu’est-ce qu’un “bottleneck” dans le pipeline ?  

---

## 6.3 Mémoire cache et hiérarchie / Cache Memory and Hierarchy  

6.3.1 – Qu’est-ce qu’un cache L1, L2, L3 ?  
6.3.2 – Quelle est la différence entre cache instruction et cache data ?  
6.3.3 – Qu’est-ce que la “locality of reference” ?  
6.3.4 – Quelle est la différence entre localité spatiale et temporelle ?  
6.3.5 – Qu’est-ce qu’un cache line ?  
6.3.6 – Qu’est-ce que le cache associatif ?  
6.3.7 – Quelle est la différence entre direct-mapped et fully associative ?  
6.3.8 – Qu’est-ce qu’un TLB (Translation Lookaside Buffer) ?  
6.3.9 – Quelle est la différence entre cache write-through et write-back ?  
6.3.10 – Qu’est-ce que la cohérence de cache ?  
6.3.11 – Quelle est la différence entre protocole MESI et MOESI ?  
6.3.12 – Qu’est-ce qu’une invalidation de ligne cache ?  
6.3.13 – Qu’est-ce qu’un cache inclusive vs exclusive ?  
6.3.14 – Quelle est la différence entre cache partagé et privé ?  
6.3.15 – Qu’est-ce que la politique de remplacement (LRU, FIFO) ?  
6.3.16 – Qu’est-ce qu’un cache prefetcher ?  
6.3.17 – Qu’est-ce qu’un “cache miss” ?  
6.3.18 – Quelle est la différence entre cold, capacity et conflict miss ?  
6.3.19 – Qu’est-ce qu’un “write allocate” ?  
6.3.20 – Quelle est la différence entre DRAM et SRAM ?  

---

## 6.4 Parallélisme et multithreading / Parallelism and Multithreading  

6.4.1 – Qu’est-ce que le parallélisme d’instructions (ILP) ?  
6.4.2 – Quelle est la différence entre ILP et DLP ?  
6.4.3 – Qu’est-ce que le multithreading matériel (SMT) ?  
6.4.4 – Quelle est la différence entre SMT et multicœur ?  
6.4.5 – Qu’est-ce que l’hyper-threading ?  
6.4.6 – Quelle est la différence entre “hardware threads” et “software threads” ?  
6.4.7 – Qu’est-ce qu’un core physique ?  
6.4.8 – Quelle est la différence entre core logique et physique ?  
6.4.9 – Qu’est-ce qu’une topologie NUMA ?  
6.4.10 – Quelle est la différence entre latence locale et distante dans NUMA ?  
6.4.11 – Qu’est-ce que la synchronisation inter-core ?  
6.4.12 – Qu’est-ce que la barrière mémoire entre threads ?  
6.4.13 – Qu’est-ce que le “cache coherence protocol” ?  
6.4.14 – Qu’est-ce qu’un “spinlock” matériel ?  
6.4.15 – Quelle est la différence entre lock-free et wait-free ?  
6.4.16 – Qu’est-ce que le “false sharing” entre threads ?  
6.4.17 – Pourquoi aligner les structures sur une ligne de cache ?  
6.4.18 – Qu’est-ce que la granularité de parallélisme ?  
6.4.19 – Quelle est la différence entre synchronisation fine et grossière ?  
6.4.20 – Qu’est-ce qu’un “thread affinity” ?  

---

## 6.5 Gestion des instructions et prédiction / Instruction Control and Prediction  

6.5.1 – Qu’est-ce qu’un “branch predictor” ?  
6.5.2 – Quelle est la différence entre prédicteur statique et dynamique ?  
6.5.3 – Qu’est-ce qu’un BTB (Branch Target Buffer) ?  
6.5.4 – Qu’est-ce qu’un “return address stack” ?  
6.5.5 – Quelle est la différence entre misprediction et flush du pipeline ?  
6.5.6 – Qu’est-ce que la “speculative execution” ?  
6.5.7 – Qu’est-ce que la vulnérabilité Spectre ?  
6.5.8 – Qu’est-ce que la vulnérabilité Meltdown ?  
6.5.9 – Quelle est la différence entre isolation matérielle et logicielle ?  
6.5.10 – Qu’est-ce que l’exécution prédictive dans les CPU modernes ?  
6.5.11 – Qu’est-ce qu’un “micro-op cache” ?  
6.5.12 – Qu’est-ce que la fusion d’instructions (macro-fusion) ?  
6.5.13 – Qu’est-ce que la décodification multiple ?  
6.5.14 – Quelle est la différence entre micro-ops et macro-instructions ?  
6.5.15 – Qu’est-ce que le “instruction retirement” ?  
6.5.16 – Qu’est-ce que le prefetch d’instructions ?  
6.5.17 – Quelle est la différence entre pipeline fetch et decode ?  
6.5.18 – Qu’est-ce que le “control flow speculation” ?  
6.5.19 – Qu’est-ce qu’un prédicteur de branche bimodal ?  
6.5.20 – Qu’est-ce qu’un “tournament predictor” ?  

---

## 6.6 Communication et cohérence mémoire / Communication and Memory Coherency  

6.6.1 – Qu’est-ce que la cohérence mémoire ?  
6.6.2 – Quelle est la différence entre cohérence et consistance ?  
6.6.3 – Qu’est-ce qu’un modèle mémoire faible ?  
6.6.4 – Quelle est la différence entre modèle mémoire séquentiel et relâché ?  
6.6.5 – Qu’est-ce que la barrière mémoire (memory fence) ?  
6.6.6 – Qu’est-ce que la synchronisation entre processeurs ?  
6.6.7 – Quelle est la différence entre “cache flush” et “cache invalidate” ?  
6.6.8 – Qu’est-ce que la communication inter-core ?  
6.6.9 – Quelle est la différence entre interconnect ring et mesh ?  
6.6.10 – Qu’est-ce qu’un bus cohérent ?  
6.6.11 – Qu’est-ce que le protocole MESIF ?  
6.6.12 – Quelle est la différence entre communication point-à-point et broadcast ?  
6.6.13 – Qu’est-ce qu’un snoop filter ?  
6.6.14 – Qu’est-ce qu’un contrôleur mémoire intégré (IMC) ?  
6.6.15 – Quelle est la différence entre DDR4 et DDR5 ?  
6.6.16 – Qu’est-ce que le “memory prefetcher” matériel ?  
6.6.17 – Qu’est-ce qu’un contrôleur NUMA ?  
6.6.18 – Quelle est la différence entre PCIe et QPI ?  
6.6.19 – Qu’est-ce qu’un “memory latency monitor” ?  
6.6.20 – Qu’est-ce que la topologie d’interconnexion “Infinity Fabric” d’AMD ?  
