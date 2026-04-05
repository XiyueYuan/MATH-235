### Markov Chain

__Definition 1.__ A __stochastic process__ is a collection of random variable ${X_t: t \in T}$ where each $X_t$ takes values in a set $S$
- Discrete time: $T = \mathbb{N}_0 = \{0, 1, 2, ...\}$ ($\mathbb{N}_0$: start from 0)
- Discrete space: $S$ is countable, e.g. $S = \mathbb{Z}, S = \mathbb{Z}^2, S = \{1, ..., N\}$
- Continuous time: $T = [0, \infty)$
- Continuous space: $S = \mathbb{R}^d$， for some $d \in \mathbb{N}$
  
Below, we will write our stochastic process as $\{X_n\}_{n \in \mathbb{N}}$

__Example 1.__ In probability theory, we study $\{X_n\}$, a sequence of independent random variables 
__Example 2.__ In stochastic process, let $\{\xi_n\}_{n \in \mathbb{N}}$ be a sequence of independent, i.i.d random variables taking values in $\mathbb{R}$, i.e. $\xi_n \in \mathbb{R}$. Let $X_0 = 0$ and $X_n = \sum_{j = 1}^{n}\xi_j$, then we have $X_{n + 1} = X_n + \xi_{n + 1}$
__Example 3.__ By conditional probability: $P[A \cap B] = P[A \mid B]P[B]$,
$$
\begin{aligned}
P[X_0=s_0, \dots, X_n=s_n] &= P[X_n=s_n \mid X_0=s_0, \dots, X_{n-1}=s_{n-1}] \\
&\quad \times P[X_0=s_0, \dots, X_{n-1}=s_{n-1}]
\end{aligned}
$$ 

$$
\begin{equation}
\begin{aligned}
P[X_0=s_0, \dots, X_n=s_n] &= P[X_n=s_n \mid X_0=s_0, \dots, X_{n-1}=s_{n-1}] \\
&\times P[X_{n-1}=s_{n-1} \mid X_0=s_0, \dots, X_{n-2}=s_{n-2}] \\
&\quad \vdots \\
&\times P[X_1=s_1 \mid X_0=s_0] \\
&\times P[X_0=s_0]
\end{aligned}
\tag{1.1}
\end{equation}
$$
__Definition 2.__ A stochastic process $\{X_n\}$ is called a Markov process if $\forall n \in \mathbb{N}, \forall s_0, ..., s_n \in S$ 
$$
P[X_n = s_n \mid X_0 = s_0, ..., X_{n - 1} = s_{n - 1}] = P[X_n = s_n \mid X_{n - 1} = s_{n - 1}]
$$
- We define $P(x, y):= P[X_1 = y | X_0 = x], \forall x, y \in \mathbb{S}$
- Therefore, the conditional probability (1.1) in markov property becomes 
$$
\begin{aligned}
P(X_0=s_0, \dots, X_n=s_n)
&= P(X_n=s_n \mid X_{n-1}=s_{n-1}) \\
&\quad \times P(X_{n-1}=s_{n-1} \mid X_{n-2}=s_{n-2}) \\
&\quad \cdots \\
&\quad \times P(X_1=s_1 \mid X_0=s_0) \\
&\quad \times P(X_0=s_0) \\
&= P(X_0=s_0)\prod_{k=1}^{n} p(s_{k-1}, s_k)
\end{aligned}
$$

__Example 4.__ A __graph__ $G$ is a collection of vertices $V(G)$  with edges $E(G)$, the __simple random walk__ on $G$ with markov chain $\{X_n\}$, where $S = V(G)$, such that $X_{n + 1}$ is one of the neighboring vertices of $X_n$, chosen uniformly at random. For each $x, y \in V(G)$, 
$$
p(x, y) = 
\begin{cases}
\frac{1}{\deg(x)}, & \text{if } (x, y) \in E(G) \\
0, & \text{otherwise}
\end{cases}
$$

__Proposition 1.__ 
We define the n-step transition probabilities
$$P_n(x,y) := P[X_n = y \mid X_0 = x]
$$
$\forall n, m \in \mathbb{N}, \forall x, y \in S$, 
$$
p^{m + n}(x, y) = \sum_{z \in S}p^n(x, z)p^m(z, y)
$$

Proof: 
$$
P[X_{n + m} = y \mid \ X_0 = x] = \sum_{z \in S}P[X_{n + m} = y, X_n = z \mid X_0 = x]
$$

$$
\text{According to Total Probability Theory, }
\\
P[A, B \mid C] = P[A \mid B, C] \cdot P[B \mid C]
$$

$$
P[X_{n + m} = y \mid \ X_0 = x] = \sum_{z \in S}P[X_{n + m} = y \mid X_n = z, X_0 = x]\cdot P[X_n = z \mid X_0 = x]
$$

$$
\text{According to Markov Property, }P[X_{n + m} = y \mid X_n = z, X_0 = x] = P[X_{n + m} = y \mid X_n = z]
$$

$$
\text{Therefore, }P[X_{n + m} = y \mid \ X_0 = x] = \sum_{z \in S}P[X_n = z \mid X_0 = x] \cdot P[X_{n + m} = y \mid X_n = z]
$$

$$
P[X_{n + m} = y \mid \ X_0 = x] = \sum_{z \in S}p^n(x, z)p^m(z, y)
$$

__Definition 3.__ The __Transition Matrix__ is the $N \times N$ matrix $P$, where $$\sum_{j \in S}p(i, j) = 1$$

__Example 5.__ Given transition matrix P, find $T^2_{1, 2}$
$$
P = \begin{pmatrix}
0.5 & 0.3 & 0.2 \\
0.1 & 0.6 & 0.4 \\
0.4 & 0.2 & 0.4
\end{pmatrix}
$$

Using CK-equation, we have $P^{n + m}(x, y) = \sum_{z \in S}p^n(x, z)p^m(z, y)$
$$
T^2_{1, 2} = \sum_{z = 1}^{3}p^1(1, z)p^2(z, 2) = 0.37
$$

### Recurrence and Transience 
__Definition 4.__ Two states, $x, y \in S$ __communicate__ if $\exists m, n \ge 0$, such that $p^n(x, y) > 0$ and $p^m(y, x) > 0$. In this case, we write $x \leftrightarrow y$.
If $x, y \in S$ communicates, then they are 
- Reflective: $x \leftrightarrow x$, since $p^0(x, x) = 1$
- Symmetric: if $x \leftrightarrow y$, then $y \leftrightarrow x$
- Transitive: if $x \leftrightarrow y$ and $y \leftrightarrow z$, then $x \leftrightarrow z$

Proof(Transitivity):
$$
\text{Given }p^n(x, y) > 0, p^l(y, z) > 0, \exists n, l \ge 0
$$

$$
p^{n + l}(x, z) = \sum_{w \in S}p^n(x, w)p^l(w, z) \ge p^n(x, y)p^l(y, z) > 0
$$

__Definition 5.__ Communication classes
- If $x \leftrightarrow y, x, y \in C$

- Recurrent Class: $\forall x \in C, y \notin C, p(x,y) = 0$

- Transient Class: $\exists x \in C, y \notin C, p(x, y) > 0$

__Definition 6.__ A Markov chain is __irreducible__ if there is only one communication class(then the only class is recurrent): 
$$
\text{Irreducible} \implies S = C \\
\implies \{y : y \notin C\} = \emptyset \\
\implies \forall x \in C, \sum_{y \notin C} p(x, y) = 0 \implies C \text{ is recurrent.}
$$

__Example 6.__ Consider a random walk on a graph $G$, if $x \leftrightarrow y$, then $x, y \in C$, the random walk is irreducible if $\forall x, y \in S, \exists n \ge 0$ such that $p^n(x, y) > 0$ 
$$
P = \begin{pmatrix}
1/5 & 1/5 & 0 & 0 & 3/5 \\
0 & 0 & 0 & 0 & 1 \\
0 & 0 & 1/2 & 1/2 & 0 \\
0 & 0 & 1/4 & 3/4 & 0 \\
1/2 & 1/4 & 1/4 & 0 & 0
\end{pmatrix}
$$

$$
S \in \{1, 2, 3, 4, 5\}, C_1 = {1, 2, 5}, C_2 = {3, 4}
$$

$C_1$ is transient, $C_2$ is recurrent.

__Example 7.__ Consider the random walk $S = \{0, 1, 2, ..., N\}$ with absorbing boundary, which $p(0, 0) = 1, p(N, N) = 1$
- $\{0\}$ and $\{N\}$ are recurrent 

- $\{1, ..., N - 1\}$ is transient

__Proposition 2.__ 
Assume $S$ is finite, if $C$ is a recurrent communication class, then if $\{X_n\}$ starts in $C$, with probability 1 $\{X_n\}$ visits each state in $C$ infinitely many times
$$
P[X_n = y \ \text{for infinitely many n} \mid X_0 = x] = 1
$$

__Proposition 3.__ Assumei $S$ is finite, if $C$ is a transient communication class, then with probability 1 $X $ eventually leaves $C$ and never returns 
$$
P_x(\text{eventually leaves C and never returns}) = 1, x \in C
$$

$$
P(\text{no hit in } k \text{ blocks}) \le (1-q)^k
$$

$$
(1-q)^k = e^{k \log(1-q)}
$$

$$
c := -\frac{\log(1-q)}{n} > 0
$$

$$j \approx nk \Rightarrow k \approx \frac{j}{n}
$$

$$
(1-q)^k
= (1-q)^{j/n}
= e^{\frac{j}{n}\log(1-q)}
= e^{-cj}
$$

$$
P(\text{hit before time } j \mid X_0 = x)
\;\ge\;
1 - e^{-cj}
$$

### Strong Markov Property 
__Definition 7.__ A random time $\tau \in \mathbb{N}_0 \cup \{\infty\}$ ($\tau$ takes values in $\{0,1,2,\dots\}$ or $\infty$, where $\infty$ indicates that the event never occurs) is called a __stopping time__ if $\forall n \in \mathbb{N}_0$, the event $\{\tau = n\}$ is determined by $X_0, ..., X_n$
- $\{\tau \le n\} = \bigcup_{j = 0}^{n}{\tau = j}$, and $\{\tau = n\} = \{\tau \le n\} \setminus \{\tau \le n - 1\}$

- $\{\tau > n\} = \{\tau \le n\}^c$
  
- $\{\min\{\tau_1, \tau_2\} \le n\} = \{\tau_1 \le n\} \cup \{\tau_2 \le n\}$

- $\{\min\{\tau_1, \tau_2\} \ge n\} = \{\tau_1 \le n\} \cap \{\tau_2 \le n\}$

__Theorem 1.__ Let $n \ge 0, m \ge 1, x_0, ..., x_n \in S, y_0, ..., y_m \in S$
$$
P[X_{\tau + 1} = y_1, ..., X_{\tau + m} = y_m \mid X_0 = x_0, ..., X_{\tau} = x_n]
$$

$$
= P[X_1 = y_1, ..., X_m = y_m \mid X_0 = x_n]
$$

### Periodicty 
__Definition 8.__ For $x \in S$, the __period__ of $x$ is the greatest common divisor ($gcd$) of
$$
J_x := \gcd \{n \ge 1: p^n(x, x) > 0\}
$$
Consider a random walk: 
$$
\begin{cases}
p_{x, x + 1} = \frac{1}{2} \\
p_{x, x - 1} = \frac{1}{2}
\end{cases}
$$
Start from 0, $\{n: X = 0\} = 0, 2, 4, 6, ..., J_x = gcd\{n \ge 1: p^n(x, x) > 0\} = 2$, therefore $\lim_{n \to \infty}p^n$ is not convergent.

To solve this, we introduce laze random walk, which makes the markov chain __aperiodic__
$$
P_{lazy} = \frac{1}{2}I + \frac{1}{2}P
$$

$$
1 \in J_x:= \{n \ge 1: p^n(x, x) > 0\}, d(x) = 1
$$

__Definition 9.__ __Invariant probability vector__ satisfies: 
$$
\pi P = \pi 
$$

$$
\text{Therefore, } \pi P^n = \pi
$$

$$
\text{To get }\pi, \sum_{i \in S}\pi_i = 1, \pi P = \pi
$$

__Theorem 2.__ If a Markov chain is finite and irreducible, then all states are positive recurrent

### Review 
__Formula 1.__ Stirling Formula 
$$
n! \sim \sqrt{2\pi n}\left(\frac{n}{e}\right)^n
$$

__Question 1.__ Prove a markov chain is recurrent 
- $$
\text{Define } T_i = \inf \{n \ge 1: X_n = i\}
$$

$$
\text{We have } P(T_i < \infty) = 1
$$

- $$ P_i(X_n = i \ \text{i.o.}) = 1, \text{i.o. = infitinely often}$$ 

- $$
p^n(i, i) = P_i(X_n = i)
$$

$$
\sum_{n = 0}^{\infty}p^n(i, i) = \infty  \ \text{if recurrent}
$$

$$
\sum_{n = 0}^{\infty}p^n(i, i) < \infty  \ \text{if transient}
$$

__Example 1.__ Consider a one-dimension random walk,$ S = \{X_n\}$, start from $n = 0$
$$
\begin{cases}
p_{i, i + 1} = \frac{1}{2}\\
p_{i, i - 1} = \frac{1}{2}
\end{cases}
$$

$$
p^{2n}(0, 0) = \binom{2n}{n}\left(\frac{1}{2}\right)^{2n}
$$

$$
\text{By Stirling formula, }p^{2n}(0, 0) \sim \frac{4^n}{\sqrt{\pi n}}
$$

__Question 2.__ Prove a Markov Chain is irreducible
- $\forall i, j \in S, \exists n \ge 0$
$$
p^n(i, j) > 0
$$

__Note 1.__ If a Markov Chain is irreducible, it means there exists only on communication class, but the class itself is not necessarily __recurrent__

__Proof 1.__ Prove $X_n \in \mathbb{Z}$, one-dimensional random walk is irreducible and transient, in which
$$
P(X_{n + 1} = X_n + 1) = p, \ P(X_{n + 1} = X_{n} - 1) = q = 1 - p, \ p \neq \frac{1}{2}
$$
To prove it is irreducible, it satisfies 
$$
\forall i, j \in \mathbb{Z}, \ n \ge 0, \ p^n(i, j) > 0
$$
For the one-dimensional random walk on $\mathbb{Z}$, we have 
$$
P(x, x + 1) = p > 0, P(x, x - 1) = q = 1 - p > 0
$$
If $j > i$, then by taking $j - i$ successive steps to the right, we get
$$
p^{j - i}(i, j) \ge p^{j - i} > 0
$$
If $j < i$, then by taking $i - j$ successibe steps to the left, we get

$$
p^{i - j}(i, j) \ge p^{i - j} > 0
$$
Thus for every $i, j \in \mathbb{Z}$, there exists $n \ge 0$ such that $p^n(i, j) > 0$, hence the chain is irreducible

To prove it is transient, we know 
$$
p^{2n}(i, i) = \binom{2n}{n}(pq)^n
$$

Therefore, 
$$
\sum_{n = 0}^{\infty}p^n(0, 0) = \sum_{m = 0}^{\infty}\binom{2m}{m}(pq)^m
$$

We know 
$$
\binom{2m}{m} \sim \frac{4^m}{\sqrt{\pi m}}
$$

Therefore,
$$
\sum_{n = 0}^{\infty}p^n(0, 0) \sim \sum_{m = 1}^{\infty}\frac{(4pq)^m}{\sqrt{m}}
$$

Because $p \ne \frac{1}{2}, p < 1, q < 1$
$$
4pq < 1
$$

$(4pq)^m$ decay exponentially, hence 
$$
\sum_{n = 0}^{\infty}p^n(0, 0) < \infty
$$

__Question 2.__ Prove a markov chain is period / aperiodic 
$$
d(i) = \gcd \{n \ge 1: p^n(i, i) > 0\}
$$

- $d(i) = 1 \to$ aperiodic
- $d(i) > 1 \to$ periodic 

- Situation 1: $p(i, i) > 0$

- Situation 2: Find $m, n \in \mathbb{Z}$ 
$$
\exists m, n \in \mathbb{Z}, s.t.\ \gcd (m, n) = 1
$$

__Question 3.__ Ergodic = irreducible + aperiodic + finite space 
If a markov chain is ergodic: 
(1.) There exists only stationary distribution
$$
\pi P = \pi 
$$
(2.) Convergent 
$$
P^n(x, y) \to \pi_y
$$
(3.) Time average = Space average 
$$
\frac{1}{n}\sum_{t = 1}^{n}f(X_t) \to \sum_y \pi_yf(y)
$$
