### Countably infinite state space
Suppose that the state space $S$ is countably infinite (discrete, countable, but infinite)

__Definition 2.__ $\{X_n\}$ is irreducible if for each $x, y \in S, \exists n$ such that $p^n(x, y) > 0$ 
__Definition 3.__ A state $x \in S$ is recurrent if 
$$
P[\exists \not ={}\text{infinitely many } n \ge 1 \ \text{s.t. } X_n = x \mid X_0 = x] = 1
$$ 

and transient otherwise

- Notice that unlike for finite state space, when $S$ is infinite reducible does not imply recurrent

__Proposition 1.__ If $\{X_n\}$ is irreducible, then either every state is recurrent or every state is transient 

__Example 1.__ Consider the Markov chain with state space $\{0, 1, 2, ...\}$ and transition probabilities 
$$
p(x, 0) = \frac{1}{x + 2},\quad p(x, x + 1) = 1 - \frac{1}{x + 2}
$$

Assume $X_0 = 0, T^+_0:= \inf\{n > 0: X_n = 0\}$,
$$
P(T^+_0 > n) = \prod_{i =0}^{n - 1}\frac{i + 1}{i + 2} = \frac{1}{n + 1} \implies P(T^+_0 = \infty) = 0
$$ 

$X_n \le n$, and we have
$$
p(X_{n + 1} = 0 \mid X_n) = \frac{1}{X_n + 2} \ge \frac{1}{n + 2}
$$

We get
$$
p^n(0, 0) \ge \frac{1}{n + 2}
$$

Hence, 
$$
\sum_{n = 0}^{\infty}p^n(0, 0) \ge \sum_{n = 0}^{\infty}\frac{1}{n + 2} = \infty
$$

Therefore, the Markov chain is recurrent 

### Biased Random Walk
Consider the biased random walk on $\mathbb{Z}$, 
$$
p(x, x + 1) = p, \quad p(x, x - 1) = 1 - p, \quad \forall x \in \mathbb{Z}
$$

Let $N \ge 1$. We are studying $P[X \ \text{hits } N \  \text{before } \ 0 \mid X_0  = x]$ For each $\{1, ..., N - 1\}$, according to hitting time, we have 
$$
h(0) = 0, \quad h(N) = 1
$$

$$
h(x) = ph(x + 1) + (1 - p)h(x - 1)
$$

To solve this equation, let $h(x) = \lambda^i$
$$
\lambda^i = p\lambda^{i + 1} + (1 + p)\lambda^{i - 1}
$$

$$
px^2 - x + (1 - p)= 0
$$

$h(x) = A\lambda_1^x + B\lambda_2^x$, therefore, 
$$
x_1 = 1, \quad x_2 = \frac{1 - p}{p}
$$

$$
h(x) = A + B\left(\frac{1 - p}{p}\right)^N
$$

We get
$$
B = \frac{1}{\left(\frac{1 - p}{p}\right)^N - 1}
$$

Hence, 
$$
P[X \ \text{hits } N \ \text{before } \ 0 \mid X_0  = x] = h(x) = \frac{\left(\frac{1 - p}{p}\right)^x - 1}{\left(\frac{1 - p}{p}\right)^N - 1}, \quad p\neq \frac12
$$

When $x = \frac12$, 
$$
h(x) = \frac12h(x + 1) + \frac12h(x - 1)
$$

$$
h(x) = \frac{x}{N}
$$

__Proposition 2.__
For $x \ge 1$, 
$$
P[X \ \text{hits } 0 \mid X_0 = x] = \begin{cases}1, \quad p \le 1/2 \\
((1 - p)/p)^x, \quad p > 1/2
\end{cases}
$$
Proof.
Let $\tau = \inf\{n \ge 0: X_n = 0\}$, from previous we have 
$$
P(\tau_N < \tau_0) = \begin{cases}
\frac{\left(\frac{1 - p}{p}\right)^x - 1}{\left(\frac{1 - p}{p}\right)^N - 1}, \quad p\neq \frac12
\\
\frac{x}{N}, \quad p = \frac12
\end{cases}
$$

Now we need $P(\tau_0 < \infty)$, first we look at $P_x(\tau_N > \tau_0) = 1 - P(\tau_N < \tau_0)$, let $r = \frac{1 - p}{p}$
- When $p > \frac12$, $0 < r < 1, N \to \infty$
$$
P_x(\tau_N < \tau_0) = \frac{r^x - 1}{r^N - 1} \to 1 - r^x
$$

Because $\{\tau_N < \tau_0\}^c = \{\tau_0 < \tau_N\}$

Therefore, $\tau_n \to \infty$
$$
P_x(\tau_0 < \infty) \to 1 - (1 - r^x) = \left(\frac{1 - p}{p}\right)^x, \quad p > \frac12
$$

- When $p < \frac12, r > 1$
$$
\lim_{N \to \infty}P_x(\tau_N < \tau_0) = 0
$$

Hence,
$$
P_x(\tau_0 < \infty) = 1
$$

- When $p = \frac12, P_x(\tau_N < \tau_0) = \frac{x}{N}$, hence,
$$
P_x(\tau_0 < \tau_N) = 1 - \frac{x}{N}
$$

When $N \to \infty$, 
$$
P_x(\tau_0 < \infty) = 1
$$

Therefore, we can conclude that, for $x \ge 1$
$$
P[X \ \text{hits } 0 \mid X_0 = x] = \begin{cases}1, \quad p \le 1/2 \\
((1 - p)/p)^x, \quad p > 1/2
\end{cases}
$$

Based on the definition of recurrent/ transient 

- $T_x = \inf\{n \ge 1: X_n = x\}$
- $P_x(T_x < \infty) = 1$ if recurrent
- $P_x(T_x < \infty) < 1$ if transient 


### Queuing model 
Consider a queue, at each time $n \ge 1$, a new person arrives with $p \in (0, 1)$. Furthermore, if there is at least one person in the queue, then the probability of one person get serviced is $q \in (0, 1)$. These happens independently from each other in the past 
$$
p(0, 1) = p, \quad p(0, 0) = 1 - p,
$$

$$
p(x, x + 1) = p(1 - q), \quad p(x, x - 1) = q(1 - p),\quad p(x, x) = pq + (1 - p)(1 - q), \forall x \ge 1
$$

Recall that $T_x := \inf\{n \ge 1: X_n = x\}$
$$
\text{x recurrent iff} \quad P_x(T_x < \infty) = 1  
$$

$$
\text{x transient iff} \quad P_x(T_x < \infty) < 1
$$

Because the chain has self-loop, let 
$$
\tau_k = \text{the first time }X_{n - 1} \neq X_n
$$

Hence,
$$
p(x, x + 1) = \frac{p(1 - q)}{p(1 - q) + q(1 - p)}, 
\quad 
p(x, x - 1) = \frac{q(1 - p)}{p(1 - q) + q(1 - p)}
$$

Now this becomes a biased random walk, according to the formula above, we get
$$
\text{the chain is recurrent iff } p \le \frac12
$$

Hence, when $p \le q$, the markov chain is recurrent 
$$
\frac{p(1 - q)}{p(1 - q) + q(1 - p)} \le \frac12 = p \le q
$$

### Null recurrence vs. positive recurrence 
__Definition 4.__ Assume that $\{X_n\}$ is irreducible and recurrent. Let $T_x := \inf\{n \ge 1: X_n = x\}$We say that $\{X_n\}$ is null recurrent if 
$$
E_x[T_x] = \infty
$$

The markov chain is positive recurrence if 
$$
E_x[T_x] < \infty
$$

- A null recurrent Markov chain cannot have a stationary distribution 

__Example 2.__ Consider a simple symmetric random walk on $\mathbb{Z}$
$$
p(x, x + 1) = p(x, x - 1) = \frac12
$$                             
Let $\tau_0 = \inf\{n \ge 1: X_n = 0\}$, for $1 \le x \le N - 1$
$$
P_x(\tau_N < \tau_0)= \frac{x}{N}
$$

Therefore
$$
\lim_{N \to \infty}P_x(\tau_0 < \tau_N) = P_x(\tau_0 < \infty) = 1 - \frac{x}{N} \to 1, \quad x \ge 1
$$

By symmetry, the same holds for $x\le -1$. Therefore, from any $x\neq0$, the walk hits 0 with probability 1. In particular, starting from 0, the first step moves to either 1 or -1, and from there the walk returns to 0 with probability 1. Thus
$P_0(T_0<\infty)=1$.
Therefore the chain is recurrent. In infinite state space, how do we know whether this is positive recurrent or null recurrent?

- If a chain does not have a stationary distribution, then it is null recurrent

$$
\pi_y = \sum_{x \in S}\pi_xp(x, y)
$$

Hence, here we have
$$
\pi(x) = \frac12\pi(x - 1) + \frac12\pi(x + 1)
$$
Since $\pi(x)\ge0$ for all $x\in\mathbb Z$, we must have $B=0$. Thus $\pi(x)\equiv A$, a constant. This cannot be normalized on $\mathbb Z$, so no stationary distribution exists.

__Proposition 3.__ Assume that $\{X_n\}$ is irreducible. The following are equivalent
- $\{X_n\}$ is positive recurrent 
- $\{X_n\}$ has a stationary distribution $\pi$
- $\lim_{n \to \infty}\sup p^n(x, y) > 0, \forall x, y \in S$
- If $T_x = \min\{n \ge 1: X_n = x\}$, then $E[T_x \mid X_0 = x] < \infty$ for each $x \in S$

__Example 3.__ Consider the biased random walk on $\{0, 1, 2...\}$ with partially reflected boundary, which has transition probabilities 
$$
p(x, x - 1) = 1 - p, \quad p(x, x + 1) = p, \forall x \ge 1
$$

$$
p(0, 0) = 1 - p,\quad p(0, 1) = p
$$

We already know that when $p \le \frac12$, this chain is recurrent

- When $p = \frac12$, we get 
$$
p(x, x - 1) = \frac12, \quad p(x, x + 1) = \frac12, \forall x \ge 1
$$

$$
p(0, 0) = \frac12,\quad p(0, 1) = \frac12
$$

Again we have, 
$$
\pi(x) = \frac12\pi(x - 1) + \frac12\pi(x + 1)
$$
$\pi(x)\equiv A$, a constant, it does not have a stationary distribution, therefore it is __null recurrent__

- When $p < \frac12$, we have
$$
\pi(x) = p\pi(x - 1) + (1 - p)\pi(x + 1), \forall x \ge 1
$$

$$
\pi(0) = (1 - p)\pi(0) + (1 - p)\pi(1)
$$

This is the same system of linear equations, which has $x_1 = 1, x_2 = \frac{p}{1 - p}$, we have the form 
$$
\pi(x) = A + B\left(\frac{p}{1 - p}\right)^x, A, B \in \mathbb{R}
$$

To satisfy stationary distribution, 
$$
\sum_{x = 0}^{\infty}\pi(x) = \sum_{x = 0}^{\infty} A + \sum_{x = 0}^{\infty}B\left(\frac{p}{1 - p}\right)^x = 1
$$

$A$ must $= 0$, this means 
$$
B\sum_{x = 0}^{\infty}\left(\frac{p}{1 - p}\right)^x = 1
$$

Let $r = \frac{p}{1 - p}, p < \frac12$, $0 < r < \frac12$
$$
\sum_{x = 0}^{\infty}r^x = \frac{1}{1 - r}
$$

Therefore, $\pi(x)$ is a stationary distribution, and the chain is __positive recurrent__
$$
B = 1 - \left(\frac{p}{1 - p}\right), \pi(x) = \left(1 - \frac{p}{1 - p}\right)\left(\frac{p}{1 - p}\right)^x
$$

•	$p<q$: positive recurrent
•	$p=q$: null recurrent
•	$p>q$: transient

### Random Walk on $\mathbb{Z}^d$
- We view $\mathbb{Z}^d$ as a graph with edges joining all pairs of points $x, y$ with $|x - y| = 1$

__Theorem 1.__ Random walk is null recurrent for $d = 1, 2$ and transient for $d \ge 3$

- Stirling formula: 
$$
n! \sim \sqrt{2\pi n}\left(\frac{n}{e}\right)^n
$$

Hence, the one dimensional markov chain is recurrent, assume it takes $2n$ steps 
$$
\sum_{n = 0}^{\infty}p^{2n}_0(X_n = 0) \sim \sum_{n = 0}^{\infty}\frac{1}{\sqrt{\pi n}} = \infty
$$

For $k = 1, ..., d$, each step in the kth component is equal to $1$ with probability $1/2$ or $-1$ with probability $1/2$, on average if a chain takes $2n$ steps, in $d$ dimensions, it moves $\frac{n}{d}$ steps 

Hence, 
$$
\sum_{n = 0}^{\infty}p^{2n}_0(X_n = 0) \sim \sum_{n = 0}^{\infty} \left(\frac{1}{\sqrt{\pi n/d}}\right)^d
$$

Particularly, when $d = 2$
$$
\frac{1}{\sqrt{\frac{\pi}{2}}}\sum_{n = 0}^{\infty}\frac1n \to \infty
$$

when $d = 3$...
$$
\frac{1}{\sqrt{\frac{\pi}{3}}}\sum_{n = 0}^{\infty}n^{-3/2} < \infty
$$

So we conclude that, when $d \ge 3$, the random walk on d-dimensions is transient 

__Example 4.__ Consider a simple random walk starting at $0$. For a positive integer $a > 0$, let 
$$
Y_a = \# \ \text{visits in a before the random walk return to 0}
$$

Because $a > 0$, you must visit the right before visit $-1$, if you start by visiting $-1$, then $P(\tau_a < \tau_0) = 0, \tau_i := \{n \ge 1: X_n = i\}$

$$
P(Y_a > 0) = \frac12 P(Y_a > 0 \mid S_1 = 1)
$$ 

Then it returns to the property of a random walk: 
$$
P_1(\text{hits a before 0}) = P_1(\tau_a < \tau_0) = \frac{1}{a}
$$

Hence, 
$$
P(Y_a > 0) = \frac12 \cdot \frac1a = \frac{1}{2a}
$$

We want study $E[Y_a]$, by total expectation: $E[Y_a] = E[Y_a \mid Y_a > 0] P(Y_a > 0)$, now we need $E[Y_a \mid Y_a > 0]$

We can start by 
$$
P(Y_a = 1 \mid Y_a > 0) = \frac12 \cdot P(\text{0 is reached before a starting in a - 1}) = \frac12 \cdot P_{a - 1}(\tau_0 < \tau_a) 
$$

By random walk, we have 
$$
P_i(\tau_0<\tau_a)=\frac{a-i}{a}
$$

Hence, 
$$
P_{a - 1}(\tau_0 < \tau_a) = \frac{a - a + 1}{a} = \frac1a
$$

$$
P(Y_a = 1 \mid Y_a > 0) = \frac{1}{2a}
$$

We can get 
$$
(Y_a \mid Y_a > 0) \sim Geo\left(\frac{1}{2a}\right)
$$

Hence, 
$$
E[Y_a] = 1
$$

By symmetry, we have 
$$
E[Y_a] = 1, \forall a \neq 0, p = \frac12
$$