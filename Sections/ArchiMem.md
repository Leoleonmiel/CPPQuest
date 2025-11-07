# 9. Architecture mémoire  
*(Memory Architecture)*  

## 📘 Sommaire local / Local Table of Contents  
1. [9.1 Structure et hiérarchie / Structure and Hierarchy](#91-structure-et-hiérarchie--structure-and-hierarchy)  
2. [9.2 Types de mémoire / Memory Types](#92-types-de-mémoire--memory-types)  
3. [9.3 Performance et bande passante / Performance and Bandwidth](#93-performance-et-bande-passante--performance-and-bandwidth)  
4. [9.4 Gestion et allocation / Management and Allocation](#94-gestion-et-allocation--management-and-allocation)  
5. [9.5 Fiabilité et intégrité / Reliability and Integrity](#95-fiabilité-et-intégrité--reliability-and-integrity)  

---

## 9.1 Structure et hiérarchie / Structure and Hierarchy  

9.1.1 – Qu’est-ce qu’une hiérarchie mémoire ?  
9.1.2 – Quelle est la différence entre registre, cache, RAM et stockage ?  
9.1.3 – Qu’est-ce que la latence mémoire ?  
9.1.4 – Qu’est-ce que la bande passante mémoire ?  
9.1.5 – Quelle est la différence entre mémoire volatile et non volatile ?  
9.1.6 – Qu’est-ce qu’un contrôleur mémoire ?  
9.1.7 – Qu’est-ce qu’une topologie mémoire NUMA ?  
9.1.8 – Quelle est la différence entre mémoire locale et distante ?  
9.1.9 – Qu’est-ce que la cohérence cache-mémoire ?  
9.1.10 – Qu’est-ce que la hiérarchie L1/L2/L3 ?  
9.1.11 – Qu’est-ce que le “memory wall” ?  
9.1.12 – Quelle est la différence entre accès séquentiel et aléatoire ?  
9.1.13 – Qu’est-ce que la latence cachée par pipeline ?  
9.1.14 – Quelle est la différence entre DRAM et SRAM ?  
9.1.15 – Qu’est-ce qu’un canal mémoire ?  
9.1.16 – Qu’est-ce qu’un rang (rank) et une banque (bank) ?  
9.1.17 – Quelle est la différence entre architecture open-row et closed-row ?  
9.1.18 – Qu’est-ce qu’un interleaving mémoire ?  
9.1.19 – Qu’est-ce qu’un contrôleur multi-canal ?  
9.1.20 – Qu’est-ce que la latence CAS ?  

---

## 9.2 Types de mémoire / Memory Types  

9.2.1 – Qu’est-ce que la SDRAM ?  
9.2.2 – Quelle est la différence entre DDR3, DDR4 et DDR5 ?  
9.2.3 – Qu’est-ce que GDDR6 ?  
9.2.4 – Quelle est la différence entre GDDR et HBM ?  
9.2.5 – Qu’est-ce que HBM2 et HBM3 ?  
9.2.6 – Qu’est-ce qu’une mémoire LPDDR ?  
9.2.7 – Qu’est-ce qu’une mémoire VRAM ?  
9.2.8 – Quelle est la différence entre VRAM dédiée et partagée ?  
9.2.9 – Qu’est-ce qu’un “embedded DRAM” ?  
9.2.10 – Qu’est-ce que la MRAM ?  
9.2.11 – Qu’est-ce que la NVRAM ?  
9.2.12 – Quelle est la différence entre Flash NAND et NOR ?  
9.2.13 – Qu’est-ce qu’un SSD NVMe ?  
9.2.14 – Quelle est la différence entre mémoire système et mémoire graphique ?  
9.2.15 – Qu’est-ce qu’une mémoire persistante (PMEM) ?  
9.2.16 – Qu’est-ce que la DRAM 3D empilée ?  
9.2.17 – Qu’est-ce qu’un “memory cube” ?  
9.2.18 – Quelle est la différence entre LPDDR et DDR standard ?  
9.2.19 – Qu’est-ce qu’un canal large (wide I/O) ?  
9.2.20 – Quelle est la différence entre single-rank et dual-rank ?  

---

## 9.3 Performance et bande passante / Performance and Bandwidth  

9.3.1 – Qu’est-ce qu’un cycle mémoire ?  
9.3.2 – Qu’est-ce qu’un “burst length” ?  
9.3.3 – Quelle est la différence entre latence et débit ?  
9.3.4 – Qu’est-ce qu’une requête mémoire concurrente ?  
9.3.5 – Qu’est-ce que le “memory throughput” ?  
9.3.6 – Quelle est la différence entre “read latency” et “write latency” ?  
9.3.7 – Qu’est-ce que le préchargement (prefetch) ?  
9.3.8 – Qu’est-ce qu’un “memory scheduler” ?  
9.3.9 – Quelle est la différence entre banque active et inactive ?  
9.3.10 – Qu’est-ce que le tRC, tRCD et tRP ?  
9.3.11 – Qu’est-ce qu’un accès aléatoire vs séquentiel ?  
9.3.12 – Quelle est la différence entre latence fixe et variable ?  
9.3.13 – Qu’est-ce que la “row hit” et “row miss” ?  
9.3.14 – Qu’est-ce que la saturation du bus mémoire ?  
9.3.15 – Qu’est-ce que la contention mémoire ?  
9.3.16 – Quelle est la différence entre lecture anticipée et spéculative ?  
9.3.17 – Qu’est-ce qu’un “memory bottleneck” ?  
9.3.18 – Qu’est-ce que la compression de bande passante ?  
9.3.19 – Qu’est-ce qu’un contrôleur de priorité mémoire ?  
9.3.20 – Quelle est la différence entre QoS et “bandwidth reservation” ?  

---

## 9.4 Gestion et allocation / Management and Allocation  

9.4.1 – Qu’est-ce qu’un allocateur mémoire ?  
9.4.2 – Quelle est la différence entre allocation statique et dynamique ?  
9.4.3 – Qu’est-ce qu’un “page fault” ?  
9.4.4 – Qu’est-ce que la pagination (paging) ?  
9.4.5 – Quelle est la différence entre segmentation et pagination ?  
9.4.6 – Qu’est-ce qu’une table de pages ?  
9.4.7 – Qu’est-ce qu’un TLB (Translation Lookaside Buffer) ?  
9.4.8 – Qu’est-ce qu’un “page walker” ?  
9.4.9 – Qu’est-ce que la mémoire virtuelle ?  
9.4.10 – Quelle est la différence entre adresse virtuelle et physique ?  
9.4.11 – Qu’est-ce qu’un “memory allocator pool” ?  
9.4.12 – Qu’est-ce que la fragmentation mémoire ?  
9.4.13 – Qu’est-ce que la mémoire partagée entre processus ?  
9.4.14 – Quelle est la différence entre “copy-on-write” et duplication ?  
9.4.15 – Qu’est-ce qu’un “huge page” ?  
9.4.16 – Qu’est-ce que la réallocation (realloc) ?  
9.4.17 – Quelle est la différence entre malloc et mmap ?  
9.4.18 – Qu’est-ce qu’un garbage collector ?  
9.4.19 – Qu’est-ce qu’un “memory pool” ?  
9.4.20 – Qu’est-ce que la gestion d’allocation GPU ?  

---

## 9.5 Fiabilité et intégrité / Reliability and Integrity  

9.5.1 – Qu’est-ce qu’une erreur mémoire ?  
9.5.2 – Quelle est la différence entre erreur douce (soft error) et dure (hard error) ?  
9.5.3 – Qu’est-ce que le “bit flip” ?  
9.5.4 – Qu’est-ce qu’une mémoire ECC ?  
9.5.5 – Quelle est la différence entre ECC et parity ?  
9.5.6 – Qu’est-ce que la redondance mémoire ?  
9.5.7 – Qu’est-ce qu’un mécanisme de scrubbing ?  
9.5.8 – Qu’est-ce qu’un refresh DRAM ?  
9.5.9 – Qu’est-ce qu’un “retention time” ?  
9.5.10 – Qu’est-ce que la fatigue d’écriture en mémoire Flash ?  
9.5.11 – Quelle est la différence entre endurance et rétention ?  
9.5.12 – Qu’est-ce qu’un “wear leveling” ?  
9.5.13 – Qu’est-ce que la protection ECC sur GPU ?  
9.5.14 – Quelle est la différence entre ECC correcteur et détecteur ?  
9.5.15 – Qu’est-ce qu’une mémoire résiliente aux rayons cosmiques ?  
9.5.16 – Qu’est-ce qu’un “row hammer” ?  
9.5.17 – Qu’est-ce qu’une attaque side-channel mémoire ?  
9.5.18 – Quelle est la différence entre “cold boot attack” et “DMA attack” ?  
9.5.19 – Qu’est-ce qu’un test de fiabilité mémoire (memtest) ?  
9.5.20 – Qu’est-ce que la correction d’erreur multi-bit ?  
