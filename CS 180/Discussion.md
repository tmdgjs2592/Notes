10/4/2024
does every hospital get matched ? $\rightarrow$ ye
once a student gets matched, it never gets unmatched
- a student never gets worse partner
It favors hospitals

Obs 1. once s in M, it never leaves M
- used to prove that it always finds a matching

Obs 2. s's matching only improves & Obs 3. h's ony decreases
- used to prove stable matching

Completeness (matching)
Contradiction
Assume at the end, h and s are unmatched.
```
h is unmatched only if it proposes to every student and gets rejected by all of them.
s is unmatched only if it is never proposed to by hospitals.
```
$\rightarrow$ since $\exists$ s $\notin$ M, h would have to ask s, resulting in a match $\rightarrow$ contradicktion

Stability (perfect matching)
Contradicktion
ASSume $\exists$ (h,s) and (h', s') s.t h' prefers s and s prefers h'.
- h' asked s but s rejected h' bc s is with h higher on the pref list.
- $\rightarrow$ contradicktion because s prefers h'.
- s prefers h' but is with h. h' never proposed to s bc h' is already matched w s' higher on the pref list.

Proof by Induction
1. base case (n=0, n=1)
2. Inductive step 
	1. weak: true for n=k, prove $\forall$ n=k+1
	2. strong: true for n<k, prove n=k+1

Ex) Linked List Search
LL = size(N), prove that I can access any index i, $0\leq i < N$ 
Base case: i = $\varnothing$, yes because it's at the hea 
Induction: 
assume we can get the head, i=k.
Due to the ptr, we can reach k+1 and set it to the head.

Big O notation
O $\rightarrow$ asymptotic upper bound $\rightarrow$ T(n) $\leq$ O(f(n))
$\Omega$ $\rightarrow$ asymptotic lower bound $\rightarrow$ T(n) $\geq$ $\Omega$(f(n))
T(n) = O(f(n)) $\rightarrow$ running time $\rightarrow$ if T(n) = $\Omega$(f(n)) = O(f(n)); T(n) = O(n) (omega)
$\exists$ constant c > 0, $n \geq n_0 \geq 0$ 
$$$\forall _{n,c} T(n) \leq (c)f(n)$$

