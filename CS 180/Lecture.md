****
9/30/2024

**Stable Matching Problem**

Setting
Hospitals: H = {$h_1, ... ,h_n$}
Students: S ={$s_1, ... , s_n$}
$\rightarrow$ hospitals have a ranking of students and students have a ranking of hospitals
$\rightarrow$ you cannot leave out any hospitals

Matching: a set of ordered pairs H$\times$S
- every hospital h $\in$ H appears in at most one pair
- every student s $\in$ S

Perfect Matching: a set of ordered pairs, each from H$\times$S
- every hospital h $\in$ H appears exactly in one pair
- every student s $\in$ H appears exactly in one pair

ex)
S = {a,b,c}
H = {UCLA, CSULB, UCB}
Perfect matching: M = {(UCLA, a), (UCB, b), (CSULB, c)}
*more than one solution for perfect matching*

One algorithm for perfect matching: just match with each index $\rightarrow$ (i,j)

Instability: 
M = {(h, s), (h', s')}
h' prefers s and s prefers h' $\rightarrow$ instability

Stable matching: a perfect matching with no instability

Gale-Shapley Algorithm (David Gale & Lloyd Shapley)
1. M = $\varnothing$
2. While (H is unmatched and hasn't proposed to every student):
	1. Let S be the 1st student on h's list when h has not yet been proposed to
	2. if (s is unmatched)
		1. add (h,s) $\in$ M
	3. else
		1. let H' be the current partner of s
		2. If S prefers h to h', remove (h',s) from M, add (h,s) to M
		3. else, s reject h (M remains unchanged)
3. return M 

Correct algorithm
- termination
- correct output

G-S algorithm
- n hospitals and n students $\rightarrow$ $n^2$ iteration $\rightarrow$ termination

NRMP: algorithm for matching residents to hospitals
- modification of G-S
****
10/2/2024
perfect matching $\rightarrow$ no instablities
instability: if $\exists$ pair that wants to break the current partner to be with other partner.

Gale Shapley
- once a student is proposed to, they become matched and never become unmatched.
- Additionally, the sequence of hospitals that s matches with become better and better.
- The sequence of students a hospital is matched to becomes worse and worse.

**Lemma: the G-S returns a matching.**
Proof
- Every hospital h $\in$ H is paired with at least one student.
	- hospitals only get matches when unmatched
	- hospitals only gain matches when matching
- Every student s $\in$ S is paired with at least one student.
	- students only get matched if they are unmathed or they give up their old match

**Lemma: the G-S algorithm outputs a perfect matching**
Proof by contradiction
Suppose: G-S algorithm does not output a perfect matching.
We know that G-S algorithm outputs a matching from the previous Lemma.
not perfect matching $\rightarrow$ there exists a student or hospital that has not been matched.
but since there are equal number of hospitals, at least one student and one hospital that are unmatched.
Based on the algorithm, h can only be unmatched at the end of the algorithm, if they have been rejected by every student.
**student s can only be unmatched if s is never proposed to.**
$\rightarrow$ This is a contradiction, since hospitals have to ask every student to be unmatched but students have to be asked by no hospitals to be unmatched.

**Lemma: the G-S outputs a stable matching**
Proof
- By the previous lemma, the G-S outputs a perfect matching.
	-  show that there are no instabilities
- Contradiction: suppose that M has an instability
- $\rightarrow$ $\exists$ a pair (h,s) and (h', s') such that h prefers s' and s' prefers h
- Case 1: h never proposes to s'
	- since h is matched with s, h proposed to s
	- but h prefers s' and proposes in decreasing order of preference, h should also have proposed to s'.
	- $\rightarrow$ contradiction.
- Case 2: h proposes to s'
	- Since s' is not matched with h, s' rejected h in favor of some other hospital h' that s' prefers to h.
	- By obs 1, the sequence of hospitals s' is matched to gets better and better.
	- Then, s' must prefer their final partner h' to h'' and also to h.
	- $\rightarrow$ contradicktion.
-  Since we have contradictions in all cases, G-S algorithm must output a stable matching.

**Efficiencies**
- mostly concerned with runtime
	- runtime = # of "basic steps" that an algorithm takes to run in the worst case.
	- basic step = simple operation
		- reading or writing to memory or I/O
		- basic ALU operation
		- Following a pointer or arrary indexing
****
10/7/2024
Big O: $f(n) \in O(g(n))$ if there exists constants $c>0$ and $N_0 \geq 0$ such that for all $n \geq N_0$,
$f(n) \leq c \cdot g(n)$  

Properties
1) If $f_1(n) \in O(g_1(n))$ and $f_2(n) \in O(g_2(n))$ then $f_1(n) + f_2(n) \in O(max\{g_1,g_2\}(n))$ 
	- Proof 
	- $f_1(n)+f_2(n) \leq c_1 \cdot g_1(n) + c_2 \cdot g_2(n)$ 
	- $f_1(n)+f_2(n) \leq 2 max\{c_1, c_2\}\cdot max\{g_1,g_2\}$
	- $f_1(n)+f_2(n) \leq c \cdot max\{g_1,g_2\}$ 
2) If $f_1(n) \in O(g_1(n))$ and $f_2(n) \in O(g_1(n))$, $f_1(n)+f_2(n) \in O(g_1(n)g_2(n))$
3) If $f(n) \in O(g(n))$ and $g(n) \in O(h(n))$, $f(n) \in O(h(n))$ 

Lemma: for constants a,b
$$log_a(n) \in O(log_b(n))$$
Proof
$log_a(n) = \frac{log_b(n)}{log_b(a)} = (\frac{1}{log_b(a)})log_b(n)$

Smallest to Largest Growth Rate
- O(1) $\rightarrow$ constant time
- O($log^c(n))$ = $O((log(n))^c)$ where $c>0$ is a constant $\rightarrow$ polylogarithmic time
- $O(n^c)$ $\rightarrow$ polynomial time
	- if $c=1$ $\rightarrow$ $O(n)$ linear time
	- $O(nlog(n))$ 
	- if $c=2$ $\rightarrow$ $O(n^2)$ quadratic time
- $O(2^n)$ $\rightarrow$ exponential time
- $O(n!)$ $\rightarrow$ factorial time
- $O(n^n)$ ($n^n = 2^{log(n^n)}) = 2^{nlog(n)}$   

An algorithm is polynomial time if $\exists$ $c>0$ such that the run time $T(n)$ of the algorithm is $O(n^c)$.
Efficient is a polynomial algorithm.
*Running polynomial multiple times ends up polynomial.*

T(n) =$n^c$
$\rightarrow$ T(2n) = $2^cn^c$ 

Notation (similar to, but not the same)
- $f \in o(g)$ < 
- $f \in O(g)$ $\leq$
- $f \in \theta(g)$ $\approx$  
- $f \in \Omega(g)$ $\geq$
- $f \in \omega (n)$ >

$\Omega$: $f\in \Omega (g)$ if $\exists$ constants $c>0, N_0\geq 0$ such that for all $n \geq N$. $f(n) \geq cg(n)$ 
$\theta$: $f \in \theta(g)$ if $f\in o(g)$ and $f\in \Omega(g)$ 
o: $f\in o(g)$ $f(n) < cg(n)$ 
$\omega$: $f\in \omega(g)$ $f(n) > cg(n)$

Gale Shapley Algorithm
Input
- Index hospitals and students by $0,1,2,...,n-1$
- Each preference list is an array A of length n
	- $A[i]$ = ith ranked element in the preference list
- 2n total preference 
- Input size = $O(n^2)$
Output
- 2 arrays hospital and student of length n
- if $(h,s) \in M$ $hospital[s]$ = h | $student[h]=s$ 
- If h or s is unmatched, then we set the value to n
****
10/9/2024

Graph: dots and lines
- V = vertices
- E = edges 
- where each edge is (u,v) for some u, v $\in$ V

Undirected Graph 
- edges are symmetric $\rightarrow$ (2,1) and (1,2) are equivalent
- unless otherwise specified, assume the graph is undirected

Directed Graph
- Direction matters $\rightarrow$ (1,2) and (2,1) are different

*no self loop in this class ex) (1,1)*

Neighbor of v: any node u such that {u,v} is an edge in the graph
Degree of v: # of edges touching v
$$\sum_{v \in V} deg(v) = 2|E|$$
Path
- a sequence of nodes where every consecutive pair of nodes is connected by an edge.
Cycle
- a path $v_1, ..., v_k$ where $k \geq 2$ and $v_1 = v_k$ 
Connected graph
- a graph where for all vertices u and v, there's a path $(u, ..., v)$
Tree
- connected graph with no cycle
- Lemma: let G=(V,E) be a graph. Then any 2 of the following statements implies the 3rd
	1. G is conncted 
	2. G has no cycles
	3. G has |V|-1 edges
- Lemma: let G be a tree. Then, for every pair of vertices, there is exactly one path between u and v.
- Lemma: Let G be a tree. Then, removing any edge from G will make it disconnected.

Rooted Tree
- A tree where we specify one node as a root

Some Questions
- Is there a path from u to v?
- What is the shortest path from u to v?
- Is a graph connected ?

BFS
Idea: Expand outward from some node s one layer at a time.
Algorithm
1. $L_0$ ={s}
2. Mark s as discovered
3. set i = 0
4. while(L_i is not empty)
	1. $L_{i+1}$ = $\varnothing$
	2. for each node u $\in$ $L_i$
		1. for each neighbor v of u
		2. if v is not discovered
		3. mark v as discovered and add v to $L_{i+1}$

Length of a path
- number of edges in a path

Lemma: for each $i\geq 0$, layer $L_i$ produced by BFS consists of all nodes at distance exactly i from s.
Proof by induction
- Base: i=0
	- $L_0$ = {s} which is all nodes distance 0 from s.
- Inductive step: assume this holds for 0 $\leq$ i $\leq$ k.
- show it holds for k+1
	- Every node in $L_{k+1}$ is distance k+1 from S.
	- If $v \in L_{k+1}$ then there is a path of length k+1 to S
	- There must be some node in layer $L_k$ that v was a neighbor of
	- By our induction hypothesis, since u is in $L_k$ there is a length k path from s to u.
	- Thus, we can get a length k+1 path from s to v.

There is no shorter path from s to v
- Suppose for contradiction that there was a shorter path of length l<k+1 from s to v.
- Then, the distance from s to v is at most l
- Thus, by our inductive hypothesis, v should be in some layer $L_j$ where $j \leq l$.
- But we only add v to $L_{k+1}$ if it was not in a previous layer. $\rightarrow$ contradiction.

Corollary: There is a path from s to t if t appears in some layer L produced by BFS.