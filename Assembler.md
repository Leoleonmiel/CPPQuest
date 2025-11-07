# 10. Assembleur et architecture bas-niveau  
*(Assembly and Low-Level Architecture)*  

## 📘 Sommaire local / Local Table of Contents  
1. [10.1 Registres et mémoire / Registers and Memory](#101-registres-et-mémoire--registers-and-memory)  
2. [10.2 Instructions et opérandes / Instructions and Operands](#102-instructions-et-opérandes--instructions-and-operands)  
3. [10.3 Appels de fonction et pile / Function Calls and Stack](#103-appels-de-fonction-et-pile--function-calls-and-stack)  
4. [10.4 Optimisation et pipeline / Optimization and Pipeline](#104-optimisation-et-pipeline--optimization-and-pipeline)  
5. [10.5 SIMD et vectorisation / SIMD and Vectorization](#105-simd-et-vectorisation--simd-and-vectorization)  
6. [10.6 Analyse de code machine / Machine Code Analysis](#106-analyse-de-code-machine--machine-code-analysis)  

---

## 10.1 Registres et mémoire / Registers and Memory  

10.1.1 – Qu’est-ce qu’un registre général (GPR) ?  
10.1.2 – Quelle est la différence entre registre et mémoire ?  
10.1.3 – Qu’est-ce que le registre d’instruction (IP/RIP) ?  
10.1.4 – Qu’est-ce que le pointeur de pile (SP/RSP) ?  
10.1.5 – Quelle est la différence entre registre volatile et non volatile ?  
10.1.6 – Qu’est-ce qu’un registre segment ?  
10.1.7 – Qu’est-ce que le registre EFLAGS/RFLAGS ?  
10.1.8 – Quelle est la taille d’un registre sur x86_64 ?  
10.1.9 – Qu’est-ce qu’un registre étendu (XMM, YMM, ZMM) ?  
10.1.10 – Quelle est la différence entre registre float et entier ?  

---

## 10.2 Instructions et opérandes / Instructions and Operands  

10.2.1 – Quelle est la structure d’une instruction assembleur ?  
10.2.2 – Qu’est-ce qu’un opérande immédiat ?  
10.2.3 – Quelle est la différence entre MOV et LEA ?  
10.2.4 – Qu’est-ce que les instructions PUSH et POP ?  
10.2.5 – Qu’est-ce que CMP et TEST ?  
10.2.6 – Quelle est la différence entre JMP, JZ et JNZ ?  
10.2.7 – Qu’est-ce que CALL et RET ?  
10.2.8 – Qu’est-ce qu’une instruction conditionnelle ?  
10.2.9 – Quelle est la différence entre instruction arithmétique et logique ?  
10.2.10 – Qu’est-ce que NOP et pourquoi l’utiliser ?  

---

## 10.3 Appels de fonction et pile / Function Calls and Stack  

10.3.1 – Qu’est-ce que la pile d’exécution ?  
10.3.2 – Comment la pile gère-t-elle les paramètres de fonction ?  
10.3.3 – Quelle est la convention d’appel `cdecl` ?  
10.3.4 – Quelle est la convention `stdcall` ?  
10.3.5 – Quelle est la convention `fastcall` ?  
10.3.6 – Qu’est-ce que la sauvegarde du registre de base (EBP/RBP) ?  
10.3.7 – Qu’est-ce que le frame pointer et le stack pointer ?  
10.3.8 – Quelle est la différence entre `push rbp` et `mov rbp, rsp` ?  
10.3.9 – Qu’est-ce que le prologue et l’épilogue d’une fonction ?  
10.3.10 – Qu’est-ce qu’un overflow de pile ?  

---

## 10.4 Optimisation et pipeline / Optimization and Pipeline  

10.4.1 – Qu’est-ce qu’un pipeline d’instructions ?  
10.4.2 – Quelle est la différence entre fetch, decode, execute ?  
10.4.3 – Qu’est-ce qu’un stall de pipeline ?  
10.4.4 – Qu’est-ce que la prédiction de branche ?  
10.4.5 – Qu’est-ce que la spéculation d’exécution ?  
10.4.6 – Quelle est la différence entre code séquentiel et pipeline superscalaire ?  
10.4.7 – Qu’est-ce qu’un hazard (data, structural, control) ?  
10.4.8 – Quelle est la différence entre out-of-order et in-order execution ?  
10.4.9 – Qu’est-ce que le register renaming ?  
10.4.10 – Qu’est-ce que la micro-op fusion (µop fusion) ?  

---

## 10.5 SIMD et vectorisation / SIMD and Vectorization  

10.5.1 – Qu’est-ce que le SIMD ?  
10.5.2 – Quelle est la différence entre SSE, AVX et AVX-512 ?  
10.5.3 – Qu’est-ce qu’un registre vectoriel ?  
10.5.4 – Qu’est-ce que l’instruction `movaps` ?  
10.5.5 – Quelle est la différence entre instructions scalaires et vectorielles ?  
10.5.6 – Qu’est-ce qu’une opération fused multiply-add (FMA) ?  
10.5.7 – Qu’est-ce que la vectorisation automatique ?  
10.5.8 – Qu’est-ce qu’une instruction shuffle ?  
10.5.9 – Quelle est la différence entre alignement 16, 32 et 64 bits ?  
10.5.10 – Qu’est-ce que la saturation arithmétique ?  

---

## 10.6 Analyse de code machine / Machine Code Analysis  

10.6.1 – Qu’est-ce qu’un désassembleur ?  
10.6.2 – Quelle est la différence entre code assembleur et code machine ?  
10.6.3 – Qu’est-ce qu’une adresse relative (RIP-relative) ?  
10.6.4 – Qu’est-ce que le format ELF ou PE ?  
10.6.5 – Qu’est-ce qu’une section .text et .data ?  
10.6.6 – Qu’est-ce que le symbol table ?  
10.6.7 – Quelle est la différence entre instruction et micro-instruction ?  
10.6.8 – Qu’est-ce que le pipeline de décodage x86 ?  
10.6.9 – Qu’est-ce qu’un breakpoint matériel ?  
10.6.10 – Qu’est-ce qu’une instruction privilégiée ?  
