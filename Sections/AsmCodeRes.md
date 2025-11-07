# 19. Assembleur — 60 exercices avec énoncés et sections de code à corriger
*(Assembly — 60 exercises with statements and partial code to fix)*
Syntaxe : x86-64, System V ABI, AT&T (GNU as). Cible : Linux.
Format : Markdown texte (.txt), sans blocs de code, sans réponses.

---
## 19.1 Prologue/Épilogue minimal
Corriger le prologue/épilogue d’une fonction f qui retourne rdi+1 dans rax.
```
.text
.globl f
f:
    ; prologue manquant
    mov %rdi, %rax
    add $1, %rax
    ; épilogue manquant
    ret
```
---
## 19.1 Alignement de pile avant appel
Garantir alignement 16 octets avant call printf@PLT.
```
.text
.globl main
main:
    push %rbp
    mov  %rsp, %rbp
    ; ajuster %rsp ici
    call printf@PLT
    leave
    ret
```
---
## 19.1 Callee-saved non préservé
Préserver r12 et r13 autour d’un appel à helper.
```
.text
.globl work
work:
    mov %rdi, %r12
    mov %rsi, %r13
    call helper
    add %r12, %r13
    mov %r13, %rax
    ret
```
---
## 19.1 Retour dans eax vs rax
Corriger une fonction int g(int) retournant 32 bits en eax.
```
.text
.globl g
g:
    mov %edi, %rax
    add $7, %rax
    ret
```
---
## 19.1 Passage d’arguments SysV
Appeler h(a,b,c) avec a=1,b=2,c=3 dans les registres adéquats.
```
.text
.globl main
main:
    mov $1, %edi
    ; b et c manquants
    call h
    xor %eax, %eax
    ret
```
---
## 19.1 leave vs pop rbp
Remplacer une séquence incorrecte par leave; ret.
```
.text
.globl k
k:
    push %rbp
    mov  %rsp, %rbp
    ; ...
    pop  %rsp   ; BUG
    ret
```
---
## 19.1 Mauvais registre pour le retour
Corriger la fonction long add(long a,long b) qui doit retourner a+b en rax.
```
.text
.globl add
add:
    mov %rdi, %rbx
    add %rsi, %rbx
    ret
```
---
## 19.1 Écrasement de rdx non autorisé
Préserver rdx dans umul avant d’utiliser mul.
```
.text
.globl umul
umul:
    mov %rdi, %rax
    mul %rsi
    mov %rdx, %rcx ; utilisé plus loin
    ret
```
---
## 19.1 Empilement déséquilibré
Corriger un déséquilibre de pile après deux push sans pop.
```
.text
.globl t
t:
    push %rbx
    push %r12
    ; ...
    ret
```
---
## 19.1 jump hors de la fonction
Remplacer un jmp direct par une séquence sûre qui revient au call-site.
```
.text
.globl j
j:
    jmp target   ; BUG
    ret
target:
    mov $1, %eax
    ret
```
---
## 19.1 add/cmp ordre des opérandes
Corriger l’ordre AT&T dans cmp pour setl sur a<b signé.
```
.text
.globl less
less:
    mov %edi, %eax
    cmp %edi, %esi ; BUG
    setl %al
    movzx %al, %eax
    ret
```
---
## 19.1 idiv préparation
Préparer rdx:rax avec cqo avant idiv %rsi.
```
.text
.globl sdiv
sdiv:
    mov %rdi, %rax
    idiv %rsi ; manque l’extension du signe
    ret
```
---
## 19.1 mul non signé
Utiliser mul (non signé) correctement, retourner le bas 64 bits.
```
.text
.globl umul64
umul64:
    mov %rdi, %rax
    imul %rsi ; BUG signe/opcode
    ret
```
---
## 19.1 adc pour addition longue
Compléter une addition 128-bit avec adc.
```
.text
.globl add128
add128:
    ; (rsi:rdi) + (rcx:rbx) -> (rdx:rax)
    mov %rdi, %rax
    add %rbx, %rax
    ; manque la partie haute avec adc
    ret
```
---
## 19.1 sbb pour soustraction longue
Compléter une soustraction 128-bit avec sbb.
```
.text
.globl sub128
sub128:
    ; (rsi:rdi) - (rcx:rbx) -> (rdx:rax)
    mov %rdi, %rax
    sub %rbx, %rax
    ; manque la partie haute avec sbb
    ret
```
---
## 19.1 bt/bts manip bits
Utiliser bts pour mettre à 1 le bit k de *p.
```
.text
.globl setbit
setbit:
    ; rdi = p, rsi = k
    ; TODO: charger, bts, stocker si besoin
    ret
```
---
## 19.1 sar vs shr
Corriger un décalage arithmétique signé sur %edi.
```
.text
.globl arshift
arshift:
    mov %edi, %eax
    shr $3, %eax ; BUG
    ret
```
---
## 19.1 lea arithmétique
Remplacer une multiplication par 10 via lea.
```
.text
.globl times10
times10:
    mov %edi, %eax
    imul $10, %eax ; à remplacer par lea
    ret
```
---
## 19.1 test vs cmp
Utiliser test pour vérifier si %rdi est nul, et retourner 1/0.
```
.text
.globl iszero
iszero:
    cmp $0, %rdi ; BUG perf/sémantique
    sete %al
    movzx %al, %eax
    ret
```
---
## 19.1 cmov conditionnel
Utiliser cmovg pour max(a,b) signé.
```
.text
.globl max
max:
    mov %rdi, %rax
    cmp %rsi, %rdi
    ; cmov manquant
    ret
```
---
## 19.1 loop vs rcx 0
Corriger une boucle loop qui ne s’exécute pas quand rcx=0.
```
.text
.globl sum
sum:
    xor %eax, %eax
    mov %rdi, %rcx
.L1:
    add (%rsi), %eax
    add $4, %rsi
    loop .L1
    ret
```
---
## 19.1 do/while en assembleur
Implémenter do {body} while(cond) avec labels.
```
.text
.globl dowhile
dowhile:
    ; body
    ; test cond
    ; jmp si vrai
    ret
```
---
## 19.1 break/continue
Ajouter un break si *(p)==0 et continue si *(p)<0.
```
.text
.globl scan
scan:
    ; boucle sur n éléments
    ; conditions break/continue à insérer
    ret
```
---
## 19.1 saut avant label
Remplacer un saut vers un label non encore défini par une structure correcte.
```
.text
.globl fwd
fwd:
    jg .Lafter ; conditions manquantes
    ; ...
.Lafter:
    ret
```
---
## 19.1 table de sauts
Implémenter un jump table pour cases 0..3.
```
.text
.globl jt
jt:
    ; rdi contient l’index
    ; construire une table de labels et y sauter
    ret
```
---
## 19.1 cmp/jcc signé vs non signé
Corriger les jcc pour comparaison non signée a<b.
```
.text
.globl lessu
lessu:
    mov %edi, %eax
    cmp %esi, %edi
    setl %al ; BUG signé
    movzx %al, %eax
    ret
```
---
## 19.1 retard slot inexistant
Supprimer l’hypothèse de delay slot : déplacer l’instruction après jmp.
```
.text
.globl no_delay
no_delay:
    jmp .Lx
    add $1, %eax ; BUG hypothétique
.Lx:
    ret
```
---
## 19.1 boucle non bornée
Ajouter un compteur et une condition d’arrêt sûre.
```
.text
.globl spin
spin:
    jmp spin
    ret
```
---
## 19.1 boucle avec prefetch
Ajouter un prefetchnta dans une boucle de copie.
```
.text
.globl copy_pf
copy_pf:
    ; boucle de copie, insérer prefetch
    ret
```
---
## 19.1 réécriture branchless
Transformer une sélection if(a<b) en version sans branche avec cmov.
```
.text
.globl sel
sel:
    ; rdi=a, rsi=b -> rax=min(a,b)
    ret
```
---
## 19.1 offset struct
Charger p->y (struct {int x; int y;}) dans eax.
```
.text
.globl load_y
load_y:
    mov 8(%rdi), %eax ; BUG
    ret
```
---
## 19.1 accès tableau
Lire arr[i] avec i en rsi et base en rdi (int32).
```
.text
.globl geti
geti:
    mov (%rdi,%rsi,8), %eax ; BUG scale
    ret
```
---
## 19.1 écriture tableau
Écrire v dans arr[i] (int32).
```
.text
.globl seti
seti:
    mov %edx, (%rdi,%rsi,2) ; BUG scale
    ret
```
---
## 19.1 SoA vs AoS
Remplacer accès AoS par SoA pour meilleures perfs.
```
.text
.globl sum_aos
sum_aos:
    ; accès struct {x,y,z} vs trois tableaux x[], y[], z[]
    ret
```
---
## 19.1 memset byte
Implémenter memset(dst,val,n) en bytes.
```
.text
.globl myset
myset:
    ; cld ; stosb en boucle ou rep stosb
    ret
```
---
## 19.1 memcpy overlap
Corriger pour gérer overlap (memmove).
```
.text
.globl mymove
mymove:
    ; détecter overlap, choisir sens
    ret
```
---
## 19.1 atomic xchg
Implémenter int xchg(int* p,int v) atomique.
```
.text
.globl xchg32
xchg32:
    ; lock xchg %eax,(%rdi)
    ret
```
---
## 19.1 barrière mémoire
Insérer mfence/sfence/lfence selon besoin.
```
.text
.globl barrier
barrier:
    ; TODO: fence adéquate
    ret
```
---
## 19.1 TLS accès
Afficher l’adresse d’une variable TLS via %fs:.
```
.text
.globl show_tls
show_tls:
    ; mov %fs:offset, %rax
    ret
```
---
## 19.1 stack canary
Insérer/valider un stack canary simplifié.
```
.text
.globl safe_fn
safe_fn:
    ; écrire canary, vérifier avant ret
    ret
```
---
## 19.1 SSE movaps alignement
Remplacer movaps par une version tolérante à l’alignement.
```
.text
.globl load4f
load4f:
    movaps (%rdi), %xmm0 ; BUG si non aligné
    ret
```
---
## 19.1 SSE haddps somme
Sommer 4 floats en xmm0 depuis *p.
```
.text
.globl sum4f
sum4f:
    movups (%rdi), %xmm0
    ; manque deux haddps
    ret
```
---
## 19.1 AVX ymm save
Préserver ymm lors d’un appel si nécessaire (SysV).
```
.text
.globl avx_call
avx_call:
    ; TODO: sauvegarde requise ?
    call callee
    ret
```
---
## 19.1 SSE scalar mul
Calculer c = a*b en float scalaire.
```
.text
.globl fmul
fmul:
    movss (%rdi), %xmm0
    mulss (%rsi), %xmm0
    ret
```
---
## 19.1 SSE normalisation
Normaliser un vecteur 3D float chargé à *p.
```
.text
.globl normalize3
normalize3:
    ; charger, dot, rsqrt, multiplier
    ret
```
---
## 19.1 FP save/restore
Sauvegarder/restaurer l’état FPU autour d’un bloc.
```
.text
.globl fpu_blk
fpu_blk:
    ; fxsave ; ... ; fxrstor
    ret
```
---
## 19.1 xmm call-clobbered
Éviter de dépendre d’un registre xmm call-clobbered après call.
```
.text
.globl use_xmm
use_xmm:
    movaps %xmm0, %xmm1
    call g
    ; utiliser xmm0 ?
    ret
```
---
## 19.1 AVX2 gather
Utiliser vgather pour charger arr[idx[i]].
```
.text
.globl gather
gather:
    ; TODO: indices et masque
    ret
```
---
## 19.1 denormals zero
Activer DAZ/FTZ si pertinent.
```
.text
.globl fp_ctrl
fp_ctrl:
    ; modifier MXCSR
    ret
```
---
## 19.1 precision flags
Configurer l’arrondi flottant vers -inf.
```
.text
.globl fp_round
fp_round:
    ; MXCSR RC
    ret
```
---
## 19.1 syscall write
Écrire 'Hi\n' sur stdout via syscall direct.
```
.text
.globl main
main:
    ; rax=1, rdi=1, rsi=buf, rdx=len ; syscall
    ret
.data
buf: .ascii "Hi\n"
```
---
## 19.1 exit code
Terminer le programme avec code 7 via syscall.
```
.text
.globl main
main:
    ; rax=60, rdi=7, syscall
    ret
```
---
## 19.1 appel PLT correct
Appeler puts@PLT avec l’argument en rdi.
```
.text
.globl main
main:
    mov $msg, %rsi ; BUG
    call puts@PLT
    ret
.data
msg: .asciz "OK"
```
---
## 19.1 GOT relocation
Charger l’adresse de msg via RIP-relative, pas absolu.
```
.text
.globl main
main:
    mov $msg, %rdi ; BUG PIE
    call puts@PLT
    ret
.data
msg: .asciz "X"
```
---
## 19.1 PIC prologue
Éviter d’écraser %rbx réservé au GOT dans certains modèles PIC.
```
.text
.globl f
f:
    mov %rdi, %rbx ; BUG si utilisé pour GOT
    ret
```
---
## 19.1 relocation RIP
Utiliser le addressing mode disp(%rip).
```
.text
.globl show
show:
    lea msg(%rip), %rdi
    call puts@PLT
    ret
.data
msg: .asciz "rip"
```
---
## 19.1 TLS modèle
Compléter l’accès à une variable __thread.
```
.text
.globl tlsget
tlsget:
    ; mov %fs:offset, %rax
    ret
```
---
## 19.1 stack guard
Insérer un canary simple en début/fin.
```
.text
.globl guard
guard:
    ; store cookie ; ... ; verify
    ret
```
---
## 19.1 errno après syscall
Lire errno après échec d’un syscall via C wrapper.
```
.text
.globl call_open
call_open:
    ; call open@PLT ; tester rax ; consulter errno
    ret
```
---
## 19.1 section .bss et .data
Déplacer un buffer non initialisé en .bss, pas en .data.
```
.bss
buf: .space 1024
.text
.globl main
main:
    ; utiliser buf
    ret
```
---
