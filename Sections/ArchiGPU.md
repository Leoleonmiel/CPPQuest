# 7. Architecture GPU  
*(GPU Architecture and Rendering Hardware)*  

## 📘 Sommaire local / Local Table of Contents  
1. [7.1 Structure et composants du GPU / GPU Structure and Components](#71-structure-et-composants-du-gpu--gpu-structure-and-components)  
2. [7.2 Unités de calcul et SIMT / Compute Units and SIMT Execution](#72-unités-de-calcul-et-simt--compute-units-and-simt-execution)  
3. [7.3 Hiérarchie mémoire GPU / GPU Memory Hierarchy](#73-hiérarchie-mémoire-gpu--gpu-memory-hierarchy)  
4. [7.4 Gestion des threads et ordonnancement / Thread Management and Scheduling](#74-gestion-des-threads-et-ordonnancement--thread-management-and-scheduling)  
5. [7.5 Pipeline graphique matériel / Hardware Graphics Pipeline](#75-pipeline-graphique-matériel--hardware-graphics-pipeline)  
6. [7.6 Ray tracing matériel et accélération / Hardware Ray Tracing and Acceleration](#76-ray-tracing-matériel-et-accélération--hardware-ray-tracing-and-acceleration)  

---

## 7.1 Structure et composants du GPU / GPU Structure and Components  

7.1.1 – Quelles sont les unités principales d’un GPU moderne ?  
7.1.2 – Quelle est la différence entre GPU et CPU en termes d’architecture ?  
7.1.3 – Qu’est-ce qu’un SM (Streaming Multiprocessor) ?  
7.1.4 – Qu’est-ce qu’un CU (Compute Unit) ?  
7.1.5 – Quelle est la différence entre cores CUDA et ROPs ?  
7.1.6 – Qu’est-ce qu’une unité de texture (TMUs) ?  
7.1.7 – Qu’est-ce qu’une ROP (Render Output Unit) ?  
7.1.8 – Quelle est la différence entre frontend et backend GPU ?  
7.1.9 – Qu’est-ce que le rôle du command processor ?  
7.1.10 – Qu’est-ce qu’un scheduler GPU ?  
7.1.11 – Quelle est la différence entre architecture monolithique et chiplet ?  
7.1.12 – Qu’est-ce qu’un bus PCI Express ?  
7.1.13 – Qu’est-ce qu’un bus NVLink ?  
7.1.14 – Quelle est la différence entre GPU intégré et discret ?  
7.1.15 – Qu’est-ce qu’une carte GPU multi-puce ?  
7.1.16 – Qu’est-ce qu’un GPU headless ?  
7.1.17 – Quelle est la différence entre pipeline fixe et programmable ?  
7.1.18 – Qu’est-ce qu’un GPU compute-only ?  
7.1.19 – Qu’est-ce que la fonction du display engine ?  
7.1.20 – Qu’est-ce qu’un protocole de communication GPU-CPU ?  

---

## 7.2 Unités de calcul et SIMT / Compute Units and SIMT Execution  

7.2.1 – Qu’est-ce que SIMT (Single Instruction Multiple Threads) ?  
7.2.2 – Quelle est la différence entre SIMD et SIMT ?  
7.2.3 – Qu’est-ce qu’un warp ou wavefront ?  
7.2.4 – Combien de threads sont exécutés simultanément dans un warp typique ?  
7.2.5 – Qu’est-ce qu’une divergence de branche ?  
7.2.6 – Pourquoi la divergence ralentit-elle le GPU ?  
7.2.7 – Qu’est-ce qu’un registre vectoriel dans un SM ?  
7.2.8 – Quelle est la différence entre FP32, FP16, INT8 cores ?  
7.2.9 – Qu’est-ce qu’un Tensor Core ?  
7.2.10 – Quelle est la différence entre Tensor Core et CUDA Core ?  
7.2.11 – Qu’est-ce que l’accumulation FMA sur GPU ?  
7.2.12 – Qu’est-ce qu’un pipeline de calcul parallèle ?  
7.2.13 – Qu’est-ce qu’une instruction fused multiply-add ?  
7.2.14 – Qu’est-ce que la latence des unités de calcul ?  
7.2.15 – Qu’est-ce que le débit mesuré en TFLOPS ?  
7.2.16 – Qu’est-ce que la différence entre shader core et compute unit ?  
7.2.17 – Qu’est-ce que la programmation SIMT implicite ?  
7.2.18 – Qu’est-ce que le “warp scheduling ”?  
7.2.19 – Qu’est-ce que la masque d’exécution de threads ?  
7.2.20 – Pourquoi les threads GPU sont-ils légers par design ?  

---

## 7.3 Hiérarchie mémoire GPU / GPU Memory Hierarchy  

7.3.1 – Quelles sont les différentes zones de mémoire sur GPU ?  
7.3.2 – Quelle est la différence entre mémoire globale et locale ?  
7.3.3 – Qu’est-ce que la mémoire partagée (shared memory) ?  
7.3.4 – Qu’est-ce que les registres par thread ?  
7.3.5 – Qu’est-ce qu’une mémoire constante ?  
7.3.6 – Qu’est-ce qu’une texture memory ?  
7.3.7 – Qu’est-ce qu’un cache L1/L2 sur GPU ?  
7.3.8 – Quelle est la taille typique du L2 cache ?  
7.3.9 – Qu’est-ce qu’un accès mémoire coalescé ?  
7.3.10 – Pourquoi le coalescing est-il crucial ?  
7.3.11 – Qu’est-ce qu’une latence mémoire masquée ?  
7.3.12 – Quelle est la différence entre HBM2 et GDDR6 ?  
7.3.13 – Qu’est-ce qu’un bus mémoire de 384 bits ?  
7.3.14 – Qu’est-ce qu’une page mémoire GPU ?  
7.3.15 – Qu’est-ce que le “unified memory” CUDA ?  
7.3.16 – Qu’est-ce que la cohérence mémoire CPU-GPU ?  
7.3.17 – Quelle est la différence entre DMA et copy engine ?  
7.3.18 – Qu’est-ce qu’une VRAM ?  
7.3.19 – Qu’est-ce qu’un GPU memory heap ?  
7.3.20 – Qu’est-ce que la compression de framebuffer ?  

---

## 7.4 Gestion des threads et ordonnancement / Thread Management and Scheduling  

7.4.1 – Qu’est-ce qu’un bloc (block) et une grille (grid) CUDA ?  
7.4.2 – Quelle est la différence entre workgroup et workitem (OpenCL) ?  
7.4.3 – Qu’est-ce qu’un ordonnanceur de warp ?  
7.4.4 – Qu’est-ce qu’un contexte de thread GPU ?  
7.4.5 – Combien de threads peuvent être actifs dans un SM ?  
7.4.6 – Qu’est-ce que l’occupation (occupancy) ?  
7.4.7 – Pourquoi l’occupation n’est-elle pas forcément synonyme de performance ?  
7.4.8 – Qu’est-ce que le contexte switching GPU ?  
7.4.9 – Quelle est la différence entre ordonnancement coopératif et préemptif ?  
7.4.10 – Qu’est-ce qu’un barrier de synchronisation ?  
7.4.11 – Qu’est-ce qu’un warp inactive ?  
7.4.12 – Qu’est-ce qu’un kernel concurrent ?  
7.4.13 – Qu’est-ce que le stream CUDA ?  
7.4.14 – Qu’est-ce qu’un context multi-GPU ?  
7.4.15 – Qu’est-ce que le multi-instance GPU (MIG) ?  
7.4.16 – Qu’est-ce qu’un problème “warp divergent” ?  
7.4.17 – Quelle est la différence entre threads coopératifs et indépendants ?  
7.4.18 – Qu’est-ce qu’un scheduler asynchrone ?  
7.4.19 – Qu’est-ce qu’une file de commande (command queue) ?  
7.4.20 – Qu’est-ce qu’un barrier globale ?  

---

## 7.5 Pipeline graphique matériel / Hardware Graphics Pipeline  

7.5.1 – Quelles sont les étapes fixes du pipeline matériel ?  
7.5.2 – Qu’est-ce qu’un front-end de rendu ?  
7.5.3 – Qu’est-ce qu’un setup engine ?  
7.5.4 – Qu’est-ce que le rôle du rasterizer ?  
7.5.5 – Qu’est-ce qu’un ROP (Render Output Processor) ?  
7.5.6 – Quelle est la différence entre ROP et TMU ?  
7.5.7 – Qu’est-ce que la compression du z-buffer ?  
7.5.8 – Qu’est-ce qu’un early-z ?  
7.5.9 – Qu’est-ce que le tile-based rendering ?  
7.5.10 – Quelle est la différence entre immediate mode et tile mode ?  
7.5.11 – Qu’est-ce qu’un rendu de tuile (TBR) ?  
7.5.12 – Pourquoi les GPU mobiles utilisent-ils TBR ?  
7.5.13 – Qu’est-ce qu’un framebuffer compressé ?  
7.5.14 – Qu’est-ce que le “depth hierarchy” ?  
7.5.15 – Qu’est-ce qu’une pipeline multi-pass matérielle ?  
7.5.16 – Qu’est-ce que le render backend ?  
7.5.17 – Qu’est-ce que le shader core pipeline ?  
7.5.18 – Qu’est-ce que le GPU command buffer ?  
7.5.19 – Qu’est-ce qu’un tile buffer ?  
7.5.20 – Qu’est-ce que le frame merge ?  

---

## 7.6 Ray tracing matériel et accélération / Hardware Ray Tracing and Acceleration  

7.6.1 – Qu’est-ce qu’une unité RT (Ray Tracing Core) ?  
7.6.2 – Quelle est la différence entre RT Core et Tensor Core ?  
7.6.3 – Qu’est-ce qu’une acceleration structure (BVH) ?  
7.6.4 – Qu’est-ce qu’un TLAS et BLAS ?  
7.6.5 – Quelle est la différence entre traversal et intersection unit ?  
7.6.6 – Qu’est-ce qu’un ray generation shader ?  
7.6.7 – Qu’est-ce qu’un closest-hit shader ?  
7.6.8 – Qu’est-ce qu’un miss shader ?  
7.6.9 – Qu’est-ce que le pipeline RT (Vulkan/DXR) ?  
7.6.10 – Qu’est-ce que la reconstruction de BVH dynamique ?  
7.6.11 – Qu’est-ce que le refit BVH ?  
7.6.12 – Quelle est la différence entre tracing logiciel et matériel ?  
7.6.13 – Qu’est-ce que la mémoire spécifique RT ?  
7.6.14 – Qu’est-ce que la latence d’un ray query ?  
7.6.15 – Qu’est-ce qu’un shader de réflexion hybride ?  
7.6.16 – Qu’est-ce que la détection de collision basée BVH ?  
7.6.17 – Qu’est-ce que la différence entre path tracing et ray tracing temps réel ?  
7.6.18 – Qu’est-ce que le denoising matériel ?  
7.6.19 – Qu’est-ce que l’API OptiX ?  
7.6.20 – Quelle est la différence entre RT accéléré NVIDIA, AMD et Intel ?  
