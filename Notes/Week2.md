### Stationary Distribution 
__Definition 1.__ Let $\pi: S \to [0, 1]$ be a probability distribution on $S$, so that $\sum_{x \in S}\pi_x = 1$. We say that $\pi$ is __stationary__ (invarint) for $\{X_n\}$ if 
$$
\pi_y = \sum_{x \in S}\pi_xp(x, y), \forall y \in S
$$
__Example 1.__ 
$$
P = \begin{pmatrix}
0.7 & 0.3 \\
0.4 & 0.6
\end{pmatrix}, \pi = (\pi_1, \pi_2), S = \{1, 2\}
$$

$$
\pi_2 = \sum_{x \in S}\pi_xp(x, 2) = \pi_1p(1, 2) + \pi_2p(2, 2)
$$

$$
\pi_1 = \sum_{y \in S}\pi_yp(y,1) = \pi_1p(1, 1) + \pi_2p(2, 1)
$$
Equivalently, 
- If $S = \{1, ..., N\}$ and we view $\pi = (\pi_1, ..., \pi_n)$ as a row vector, then $\pi P = \pi$, $\pi$ is a left eigenvector of $P$ with eigenvalue 1

__Theorem 1.__ If $S$ is finite and $\{X_n\}$ is irreducible and aperiodic, then there is a unique stationary distribution $\pi$ for $\{X_n\}$. Furthermore, for any $x, y \in S$
$$
\lim_{n\to\infty}P[X_n = y \mid X_0 = x] = \pi_y
$$
__Proposition 1.__ Fix $z \in S$ and suppose that we start at $X_0 = z$. Let $T:= \min\{n \ge 1: X_n = z\}$ be the first time we return to z. $\{X_n\}$ is irreducible, for $x \in S$, let 
$$
\pi_x:= E[\#\{n \in \{0, ..., T - 1\}: X_n = x\}]
$$
Then,
$$
x \to \frac{\pi_x}{E[T]} 
$$
is a stationary distribution for $\{X_n\}$
Proof. 
Define 
$$
\pi_x:= E[\#\{n \in \{0, ..., T - 1\}: X_n = x\}] = E\left[\sum_{n = 0}^{T - 1}1_{X_n = x}\right]
$$

$$
= E\left[\sum_{n =0}^{\infty}1_{X_n = x, T > n}\right]= \sum_{n = 0}^{\infty}P[X_n = x, T > n]
$$
Therefore, 
$$
\sum_{x \in S}\pi_xp(x, y) = \sum_{x\in S}\sum_{n = 0}^{\infty}P[X_n = x, T > n]p(x,y)
$$
According to Markov property, 
$$
= \sum_{n = 0}^{\infty}\sum_{x \in S}P[X_n = x, T > n, X_{n + 1} = y] = \sum_{n = 0}^{\infty}P[T > n, X_{n + 1} = y]
$$
For $y \neq z$, 
$$
= \sum_{n = 0}^{\infty}P[T > n + 1, X_{n + 1} = y]
$$
Recall that
$$\pi_y = \sum_{n = 0}^{\infty}P[T > n, X_n = y]
$$
Let $m = n + 1$, then 
$$
\sum_{n = 0}^{\infty}P[T > n + 1, X_{n + 1} = y] = \sum_{m = 1}^{\infty}P[T > m, X_{m} = y]
$$
Recall that $X_0 = z$, when $m = 0, P[T > 0, X_0 = y] = 0$, therefore, 
$$
\sum_{x \in S}\pi_xp(x, y) = \pi_y, \quad y\neq z
$$
If $y = z$, we have
$$
\sum_{x \in S}\pi_xp(x, z) = \sum_{n = 0}^{\infty}P[T > n, X_{n + 1} = z] = \sum_{n = 0}^{\infty}P[T = n + 1] = 1
$$
In the time $\{0, ..., T - 1\}$, state $z$ only appears once
$$
\pi_z = E[\#\{n \in \{0, ..., T - 1\}: X_n = z\}] = 1 
$$
Therefore, 
$$
\sum_{x \in S}\pi_xp(x, z) = \pi_z
$$

__Proposition 2.__ Let $\pi$ be the stationary distribution and for $x \in S$, let $T_x = \min\{n \ge 1: X_n = x\}$ Then 
$$
\pi_x = \frac{1}{E[T_x \mid X_0 = x]} = \frac{1}{E[T_x]}
$$

__Example 2.__ Let $G = (V, E)$ be a finite, connected graph which is not bipartite. The random walk on $\{X_n\}$ on $G$ is irreducible and aperiodic. Recall that $deg(x)$ is the number of neighbors of $x$. The stationary distribution for $\{X_n\}$ is given by 
$$
\pi_x = \frac{deg(x)}{\sum_{i \in S}deg(i)} = \frac{deg(x)}{2 |E|}
$$
which $|E|$ denotes the cardinality of the set
- Undirected Graph (By Default): if $A \to B$, then $B \to A, \forall A, B \in G(V)$, and random walk on a graph with $p(x, y) = \frac{1}{deg(x)}$
- Directed Graph: if $A \to B$, not necessarily $B \to A$
Proof. 
For simple random walk on a undirected graph, 
$$
p(x, y) = \begin{cases}\frac{1}{deg(x)}, \quad x \sim y \\
0, \quad \text{otherwise}
\end{cases}
$$
Each edge is counted twice, 
$$
\sum_{x \in V}deg(x) = 2|E|
$$
Therefore, 
$$
\sum_{x \in V}\pi_x = \frac{1}{2|E|}\sum_{x \in V}deg(x) = 1
$$
To prove it is stationary, 
$$
\sum_{x \sim y}\pi_xp(x, y) = \frac{1}{2|E|}\sum_{x \sim y}deg(x)\cdot \frac{1}{deg(x)} 
$$

$$
= \frac{1}{2|E|}\sum_{x \sim y}1 = \frac{deg(y)}{2|E|} = \pi_y
$$

__Example 3.__ A queen can move any number of squares horizontally, vertically, or diagonally on an $8 \times 8$ chessboard. Let $\{X_n\}$ be the sequence of squares that results if we pick one of queen’s legal moves uniformly at random. Find
(1.) The stationary distribution 
(2.) The expected number of moves needed to return to the bottom left corner when we start there

$$
S = \begin{pmatrix}
(1, 1) & (1, 2) & \cdots & (1, 8) \\
(2, 1) & (2, 2) & \ddots & \vdots \\
\vdots & \ddots & \ddots & (7, 8) \\
(8, 1)& \cdots & (8, 7) & (8, 8)
\end{pmatrix}
$$

$$
\pi_x = \frac{deg(x)}{\sum_{i \in S}deg(i)} = \frac{deg(x)}{2 |E|}, \forall x \in S
$$

Because of the symmetry of the $8\times 8$ chessboard, it is enough to compute the degrees of the squares in the top-left $4\times 4$ block:
$$
\begin{pmatrix}
21 & 21 & 21 & 21 \\
21 & 23 & 23 & 23 \\
21 & 23 & 25 & 25 \\
21 & 23 & 25 & 27
\end{pmatrix}.
$$

By symmetry, the sum of the degrees over all $64$ squares is
$$
\sum_{(i,j)\in S}\deg(i,j)
= 28\cdot 21 + 20\cdot 23 + 12\cdot 25 + 4\cdot 27
=1456.
$$

Therefore, the stationary distribution is
$$
\pi_{i,j}=\frac{\deg(i,j)}{1456}, \qquad (i,j)\in S.
$$

$$
\pi_{i, j} = \frac{21}{1456}
$$

The expected number of moves needed to return to the bottom left corner when we start there is simply 
$$
E[T_x] = \frac{1}{\pi_{i, j}} = \frac{1456}{21}
$$

__Proposition 3. Detailed Balance__
$$
\pi_iP(i,j) = \pi_jP(j, i)
$$
This condition (local balance) guarantees a stationary distribution and implies time-reversibility.
Proof. 
$$
\pi_iP(i,j) = \pi_jP(j, i)
$$
Therefore, 
$$
\sum_{i \in S}\pi_iP(i,j) = \pi_j\sum_{i \in S}P(j, i)
$$
Because $\sum_{i \in S}P(j, i) = 1$
Therefore, we have 
$$
\sum_{i \in S}\pi_iP(i,j) = \pi_j
$$
which is the definition of the stationary distribution 

### Countably infinite state space
Suppose that the state space $S$ is countably infinite (discrete, countable, but infinite)

__Definition 2.__ $\{X_n\}$ is irreducible if for each $x, y \in S, \exists n$ such that $p^n(x, y) > 0$ 
__Definition 3.__ A state $x \in S$ is recurrent if 
$$
P[\exists \not ={}\text{infinitely many } n \ge 1 \ \text{s.t. } X_n = x \mid X_0 = x] = 1
$$ 

and transient otherwise

- Notice that unlike for finite state space, when $S$ is infinite reducible does not imply recurrent