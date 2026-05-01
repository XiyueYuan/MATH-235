__Recurrence, Transience__
Recurrent 
$$
P_x(T_x<\infty)= \sum_{n=1}^\infty P_x(T_x=n) = 1, \quad P_x(T_x = \infty)=0, \quad \sum_{n=1}^\infty p^n(x,x)=\infty
$$

Positive Recurrent 
$$
E_x[T_x] < \infty, \quad \sum_{x \in S}\pi_x = 1
$$

Null Recurrent
$$
E_x[T_x] = \sum_{n = 1}^{\infty}nP(T = n) = \sum_{n = 1}^{\infty}P(T > n) = \infty
$$

__Stationary Distribution__
Common formula
$$
\pi P = \pi, \quad \pi_j = \sum_{i \in S}\pi_i p(i, j), \quad \pi_ip(i, j) = \pi_jp(j, i)
$$

Number of arrivals before given state, $\tau = \inf\{n \ge 1: X_n = 1\}$,
$$
E[\#\{n \in \{0, 1, ..., \tau - 1\}: X_n = 0\}] = E_i\left[\sum_{n = 0}^{T_i - 1}\mathbf{1_{X_n = j}}\right] = \frac{\pi_j}{\pi_i}
$$

Long run distribution
$$
\lim_{n \to \infty}P\{X_n = i, X_{n + 1} = j, X_{n + 2} = k\} = \pi_i \cdot p(i, j) \cdot p(j, k)
$$

__Branching Process__
In a branching process, what matters is each individual’s contribution to the next generation, so in some cases $P(x, x-1)$ corresponds to $P(Y=0)$.
$$
P(\text{eventual extinction}\mid X_0=n)=q^n
$$

$$
\mu = E[Y] = \sum_{n = 0}^{\infty}np_n, \quad E[X_n] = X_0\mu^n, \quad \phi(s)=\sum_{k=0}^\infty p_k s^k = s
$$

__Poisson Process__
$$
P\{X = k\} = \frac{e^{-\lambda}\lambda^k}{k!}, X \sim \mathrm{Poi}(\lambda) \implies E[X] = Var[X] = \lambda
$$

- $X_1 \sim Poi(\lambda_1), X_2 \sim Poi(\lambda_2)$, i.i.d. $X_1 + X_2 = Poi(\lambda_1 + \lambda_2)$
- $E[X_2\mid X_1]=X_1+\lambda, \quad E[X_1\mid X_2]=\frac{X_2}{2}$
- $E[X(X-1)]=\lambda^2, \quad E[X^2]=\lambda+\lambda^2$
- $E[X_t \mid X_s]= X_s + \lambda (t-s), \quad E[X_s \mid X_t]= \frac{s}{t} X_t$
- $E[X_t] = \lambda t, \quad N_t \sim \mathrm{Poi}(\lambda t).$
- $P\{X_3 = 4 \mid X_6 = 10\} = \frac{P\{X_3 = 4, X_6 - X_3 = 6\}}{P\{X_6 = 10\}}$
- $E[T_n]=\frac{n}{\lambda}, \quad E[T_n\mid X_s=m] = s+\frac{n-m}{\lambda}$
- $E[\tau_n\mid \tau_1>t]=t+\frac{n}{\lambda}$
- $P(\tau > s + t \mid \tau > s) = P(\tau > t)$

__Markov chain__
$$
P(\tau_N < \tau_0) = \begin{cases}
\frac{\left(\frac{1 - p}{p}\right)^x - 1}{\left(\frac{1 - p}{p}\right)^N - 1}, \quad p\neq \frac12
\\
\frac{x}{N}, \quad p = \frac12
\end{cases}
$$

$$
P(\tau_0 < \infty) = \begin{cases}1, \quad p \le 1/2 \\
(\frac{1-p}{p})^x, \quad p > 1/2
\end{cases}
$$

__Random Walk__

$$
p^{(2n)}(0,0)\approx \left(\frac{1}{\sqrt{\pi n/d}}\right)^d
$$
- $d = 1, 2$, recurrent 
- $d >= 3$, transient 

__Expectation__
$$
E[X]=\sum_i E[X\mid A_i]P(A_i)
$$

- An irreducible chain is positive recurrent iff it has a stationary distribution.