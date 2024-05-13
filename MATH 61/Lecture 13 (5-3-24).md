**Counting method cont**

Ex) 
How many 8-bit strings have exactly 2 1's?
Ans: $8\choose2$

Ex)
How many solutions $(x_1, x_2, x_3)$ are there to the equation $x_1 + x_2 + x_3 = 6$ where each $x_i \in \mathbb Z_{\geq 0}$ ?
Ans: $8 \choose 2$ 
$\rightarrow$ you can think of this problem as how to place 2 bars in 8 bit string (including the bar, so 6 chars and 2 bars). 

Theorem:
Let $k,n \in \mathbb Z{>0}$. Then the number of solution to $x_1+ x_2+\dots +x_k = n$ where each $x_i \in \mathbb Z_{\geq 0}$, is given by $(n+k-1) \choose n$ =$n+k-1\choose k-1$ 

Ex)
Suppose a library has 3 types of book: CS, physics, history. Suppose the library has at least 6 copies of each book. In how many ways can we chec kout 6 books?
Ans: $8\choose2$ Same as the one above

Ex)
Suppose I have 13 donuts and 3 friends. I want to distribute the donuts to my friends in such a way that each friend gets at least 2 donuts. In how many ways can i do this ?
Ans:
First, we can set variables as following:
$$
\begin{align}
x_1 &= \text{number of donuts of first friend}\\
x_2 &= \text{number of donuts of second friend}\\
x_3 &= \text{number of donuts of third friend}
\end{align}
$$
We have the following equation,
$$x_1 + x_2 + x_3 = 13$$
Since we want each friend to get at least two donuts, $y_i = x_i +2$
Using $y_i$, the equation turns into,
$$y_1 + y_2 + y_3 = 7$$
Therefore, the answer is $9\choose2$.
