# 8. Architecture système et interaction CPU–GPU  
*(System Architecture and CPU–GPU Interaction)*  

## 📘 Sommaire local / Local Table of Contents  
1. [8.1 Interconnexion et communication / Interconnects and Communication](#81-interconnexion-et-communication--interconnects-and-communication)  
2. [8.2 Mémoire partagée et unifiée / Shared and Unified Memory](#82-mémoire-partagée-et-unifiée--shared-and-unified-memory)  
3. [8.3 Synchronisation et cohérence / Synchronization and Coherency](#83-synchronisation-et-cohérence--synchronization-and-coherency)  
4. [8.4 Gestion des ressources et scheduling / Resource Management and Scheduling](#84-gestion-des-ressources-et-scheduling--resource-management-and-scheduling)  
5. [8.5 Virtualisation et systèmes hétérogènes / Virtualization and Heterogeneous Systems](#85-virtualisation-et-systèmes-hétérogènes--virtualization-and-heterogeneous-systems)  

---

## 8.1 Interconnexion et communication / Interconnects and Communication  

8.1.1 – Qu’est-ce qu’un bus d’interconnexion ?  
8.1.2 – Quelle est la différence entre bus parallèle et série ?  
8.1.3 – Qu’est-ce que le bus PCI Express ?  
8.1.4 – Quelle est la différence entre PCIe 3.0, 4.0, 5.0, 6.0 ?  
8.1.5 – Qu’est-ce que la bande passante d’un lien PCIe x16 ?  
8.1.6 – Qu’est-ce que la latence d’un transfert PCIe ?  
8.1.7 – Qu’est-ce que NVLink ?  
8.1.8 – Quelle est la différence entre NVLink et PCIe ?  
8.1.9 – Qu’est-ce que Infinity Fabric (AMD) ?  
8.1.10 – Qu’est-ce que CXL (Compute Express Link) ?  
8.1.11 – Quelle est la différence entre CXL et PCIe ?  
8.1.12 – Qu’est-ce qu’une topologie NUMA multi-socket ?  
8.1.13 – Qu’est-ce qu’un pont PCIe (bridge) ?  
8.1.14 – Quelle est la différence entre liaison point-à-point et bus partagé ?  
8.1.15 – Qu’est-ce qu’une architecture en anneau (ring bus) ?  
8.1.16 – Qu’est-ce qu’une architecture mesh ?  
8.1.17 – Quelle est la différence entre communication synchrone et asynchrone ?  
8.1.18 – Qu’est-ce qu’un “command buffer” dans la communication CPU-GPU ?  
8.1.19 – Qu’est-ce qu’un DMA (Direct Memory Access) ?  
8.1.20 – Quelle est la différence entre DMA bloquant et non bloquant ?  

---

## 8.2 Mémoire partagée et unifiée / Shared and Unified Memory  

8.2.1 – Qu’est-ce qu’une mémoire unifiée CPU-GPU ?  
8.2.2 – Quelle est la différence entre mémoire unifiée et mémoire partagée ?  
8.2.3 – Qu’est-ce que la gestion de page unifiée (UPM) ?  
8.2.4 – Quelle est la différence entre accès unifié et copie explicite ?  
8.2.5 – Qu’est-ce que la cohérence mémoire CPU-GPU ?  
8.2.6 – Qu’est-ce qu’un “pinned memory buffer” ?  
8.2.7 – Quelle est la différence entre pageable et pinned memory ?  
8.2.8 – Qu’est-ce qu’un transfert zéro-copie ?  
8.2.9 – Qu’est-ce que le “peer-to-peer memory access” ?  
8.2.10 – Qu’est-ce qu’un “BAR” (Base Address Register) PCIe ?  
8.2.11 – Qu’est-ce que la mémoire HBM unifiée ?  
8.2.12 – Quelle est la différence entre HBM et GDDR ?  
8.2.13 – Qu’est-ce qu’un GPU NUMA-aware ?  
8.2.14 – Qu’est-ce que la cohérence via NVLink ?  
8.2.15 – Qu’est-ce que le “Unified Virtual Addressing” (UVA) ?  
8.2.16 – Qu’est-ce qu’un mapping mémoire partagé entre processus ?  
8.2.17 – Quelle est la différence entre mémoire virtuelle et physique sur GPU ?  
8.2.18 – Qu’est-ce que la pagination de mémoire GPU ?  
8.2.19 – Qu’est-ce que la compression mémoire à la volée ?  
8.2.20 – Quelle est la différence entre VRAM partagée et dédiée ?  

---

## 8.3 Synchronisation et cohérence / Synchronization and Coherency  

8.3.1 – Qu’est-ce qu’une barrière de synchronisation CPU-GPU ?  
8.3.2 – Quelle est la différence entre fence et semaphore ?  
8.3.3 – Qu’est-ce qu’un fence Vulkan ou DirectX12 ?  
8.3.4 – Qu’est-ce qu’un event GPU ?  
8.3.5 – Quelle est la différence entre synchronisation logicielle et matérielle ?  
8.3.6 – Qu’est-ce qu’une latence de synchronisation ?  
8.3.7 – Quelle est la différence entre pipeline stall et sync stall ?  
8.3.8 – Qu’est-ce que la “command queue dependency” ?  
8.3.9 – Qu’est-ce qu’une timeline semaphore ?  
8.3.10 – Quelle est la différence entre “wait” et “signal” ?  
8.3.11 – Qu’est-ce qu’une barrière mémoire ?  
8.3.12 – Qu’est-ce qu’un “flush” mémoire GPU ?  
8.3.13 – Qu’est-ce que la cohérence cache entre CPU et GPU ?  
8.3.14 – Quelle est la différence entre cohérence forte et faible ?  
8.3.15 – Qu’est-ce que la “coherency domain” ?  
8.3.16 – Qu’est-ce que la synchronisation inter-GPU ?  
8.3.17 – Quelle est la différence entre multi-GPU synchrone et asynchrone ?  
8.3.18 – Qu’est-ce que la latence de synchronisation multi-device ?  
8.3.19 – Qu’est-ce qu’un “barrier scope” ?  
8.3.20 – Qu’est-ce que la cohérence en mémoire partagée CUDA ?  

---

## 8.4 Gestion des ressources et scheduling / Resource Management and Scheduling  

8.4.1 – Qu’est-ce qu’un scheduler CPU-GPU ?  
8.4.2 – Quelle est la différence entre ordonnanceur matériel et logiciel ?  
8.4.3 – Qu’est-ce qu’un job de calcul GPU ?  
8.4.4 – Quelle est la différence entre job compute et job graphique ?  
8.4.5 – Qu’est-ce qu’une “command submission” ?  
8.4.6 – Qu’est-ce qu’une “render queue” ?  
8.4.7 – Qu’est-ce qu’un “frame graph scheduler” ?  
8.4.8 – Quelle est la différence entre priorité CPU et GPU ?  
8.4.9 – Qu’est-ce qu’un “context switch” GPU ?  
8.4.10 – Qu’est-ce qu’un GPU context preemption ?  
8.4.11 – Quelle est la différence entre scheduling coopératif et préemptif ?  
8.4.12 – Qu’est-ce que la gestion de charge GPU (load balancing) ?  
8.4.13 – Qu’est-ce que la latence de soumission (submission latency) ?  
8.4.14 – Qu’est-ce qu’un pipeline de commandes asynchrones ?  
8.4.15 – Qu’est-ce qu’un timeline scheduling ?  
8.4.16 – Quelle est la différence entre travail batché et interactif ?  
8.4.17 – Qu’est-ce que la gestion dynamique de fréquence (DVFS) ?  
8.4.18 – Qu’est-ce qu’une gestion d’énergie adaptative GPU ?  
8.4.19 – Qu’est-ce qu’une “work stealing queue” ?  
8.4.20 – Qu’est-ce que la latence de dispatch CPU-GPU ?  

---

## 8.5 Virtualisation et systèmes hétérogènes / Virtualization and Heterogeneous Systems  

8.5.1 – Qu’est-ce que la virtualisation GPU ?  
8.5.2 – Quelle est la différence entre SR-IOV et MxGPU ?  
8.5.3 – Qu’est-ce qu’un vGPU ?  
8.5.4 – Qu’est-ce qu’une virtualisation complète vs partielle ?  
8.5.5 – Quelle est la différence entre “passthrough” et “paravirtualisation” ?  
8.5.6 – Qu’est-ce que la partition logique GPU ?  
8.5.7 – Qu’est-ce qu’un “multi-instance GPU” (MIG NVIDIA) ?  
8.5.8 – Qu’est-ce que la virtualisation CPU-GPU unifiée ?  
8.5.9 – Qu’est-ce qu’un OS hétérogène (HSA) ?  
8.5.10 – Qu’est-ce que le modèle HSA de mémoire unifiée ?  
8.5.11 – Qu’est-ce que la gestion du contexte multi-tenant ?  
8.5.12 – Quelle est la différence entre contexte virtuel et physique ?  
8.5.13 – Qu’est-ce qu’un hyperviseur GPU ?  
8.5.14 – Qu’est-ce que la migration de contexte GPU ?  
8.5.15 – Qu’est-ce que la compatibilité binaire ISA GPU ?  
8.5.16 – Qu’est-ce que la virtualisation de commande graphique ?  
8.5.17 – Qu’est-ce qu’un “resource isolation domain” ?  
8.5.18 – Qu’est-ce que la supervision CPU d’un GPU partagé ?  
8.5.19 – Quelle est la différence entre GPU cloud et bare-metal ?  
8.5.20 – Qu’est-ce que la virtualisation à granularité fine (fine-grained virtualization) ?  
