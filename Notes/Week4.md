### Branching process 
__Def.__ Consider a population of individuals. We let $X_n$ denote the number of individuals at time $n$
- The number of individuals at stage $n$, $X_n$, is then a Markov chain with state space $\{0, 1, 2, ...\}$
- Note that 0 is absorbing state, if $X_n = 0, X_{n + 1} = 0$
- If $Y_1, ..., Y_k$ are independent random variables each with distribution $P\{Y_i = j\} = p_j$
- $X_{n + 1} = Y_1 + Y_2 + ... + Y_k$
$$
p(k, j) = P\{X_{n + 1} = j \mid X_n = k\} = P\{Y_1 + ... + Y_k = j\}
$$

Let $\mu$ denote the mean number of offspring produced by an individual 
$$
\mu = \sum_{i = 0}^{\infty}ip_i = E[Y]
$$

$$
E[X_{n + 1} \mid X_n = k] = E[Y_1 + ... + Y_k] = k\mu
$$ 
- The calculation of $E[X_n]$
$$
\mathbb E(X_n)
=
\sum_{k=0}^\infty \mathbb P\{X_{n-1}=k\}\,
\mathbb E(X_n\mid X_{n-1}=k) 
$$

$$
\mathbb E(X_n) = \mu\sum_{k=0}^\infty k\mathbb P\{X_{n-1}=k\} = E(X_{n - 1})
$$

Hence, 
$$
E(X_n) = \mu^nE(X_0)
$$

- If $\mu < 1$, then the mean number of offspring goes to 0 as $n$ gets large 
$$
E(X_n) \to 0, \quad \mu < 1, n \to \infty 
$$

$$
\mathbb E(X_n)=\sum_{k=0}^\infty k\mathbb P\{X_n=k\}
\ge \sum_{k=1}^\infty \mathbb P\{X_n=k\}
= \mathbb P\{X_n\ge 1\}
$$

Proof.

$$
kP(X_n = k) \ge P(X_n = k), \quad k \ge 1
$$

Hence, 
$$
\sum_{k=1}^\infty k\mathbb P(X_n=k)
\ge
\sum_{k=1}^\infty \mathbb P(X_n=k)
$$

$$
E(X_n)
\ge
\sum_{k=1}^\infty \mathbb P(X_n=k)
$$

$$
\sum_{k=1}^\infty \mathbb P(X_n=k) = P(X_n \ge 1)
$$

Therefore,
$$
E(X_n)\ge P(X_n \ge 1)
$$
If $\mu=1$, the expected population size remains constant while for $\mu > 1$, the expected population size grows. It is not so clear in these cases whether or not the population dies out with probability 1.

Below we investigate how to determine the probability that the population dies out.

We assume that:
- $p_0 > 0$: it is possible for individual to not have offspring
- $p_0 + p_1 < 1$: it is possible for individual to have more than one offspring 

$$
a_n(k)=\mathbb P\{X_n=0\mid X_0=k\}
$$

Let $a(k)$ be the probability that the population eventually dies out assuming that there are $k$ individuals initially, 
$$
a(k) = \lim_{n \to \infty}a_n(k)
$$

If the population has $k$ individuals at a certain time, then the only way for the population to die out is for all $k$ branches to die out. Since the branches act independently,
$$
a(k) = [a(1)]^k
$$

which we will denote by just $a$ and call the extinction probability
$$
a=\mathbb P(\text{population dies out}\mid X_0=1)
$$

$$
a=\sum_{k=0}^\infty
\mathbb P\{X_1=k\mid X_0=1\}
\,
\mathbb P\{\text{population dies out}\mid X_1=k\} =\sum_{k=0}^\infty p_k a^k
$$

Define PGF(probability generating function): 
- If $X$ is a random variable taking values in $\{0,1,2,\dots\}$, the generating function of $X$ is the function
$$
\phi(s)=\phi_X(s)=\mathbb E(s^X)=\sum_{k=0}^\infty s^k\mathbb P(X=k)
$$
- Note that $\phi(s)$ is an increasing function of s for $s\ge 0$ with $\phi(0)=\mathbb P\{X=0\}$ and $\phi(1)=1$

$$
\phi^1(s) = \sum_{k = 0}^{\infty}kp(x = k) = E[X] = \mu
$$

Steps: 
1. $$
\phi(s)=\sum_{k=0}^\infty p_k s^k
$$

2. $$
\mu=\phi'(1)=\sum_{k=0}^\infty k p_k
$$

3. $$a=\phi(a)$$

4. If $\mu\le 1, a = 1$; If $\mu > 1$, find the root smaller than 1 

__Example 1.__
$$
p_0 = \frac14, \quad p_1 = \frac14, \quad p_2 = \frac12 
$$

$$
\mu = 0 \times \frac14 + 1 \times \frac14 + 2 \times \frac12 = \frac54
$$

$$
\phi(s) = \sum_{k = 0}^{\infty}p_ks^k = \frac14 + \frac14s + \frac12s^2
$$

$$
\frac14 + \frac14a + \frac12a^2 = a \implies a_1 = \frac12, a_2 = 1
$$

Therefore, the probability of extinction is $\frac12$

### Poisson process 
__Definition 1.__ A random variable $X$ has the Poisson Distribution with mean $\lambda$ of 
$$
P\{X = k\} = \frac{e^{-\lambda}\lambda^k}{k!}, \qquad k=0,1,2,\dots
$$

$$
X \sim \mathrm{Poi}(\lambda) \implies E[X] = Var[X] = \lambda
$$

__Proposition.__ If $X_1 \sim Poi(\lambda_1), X_2 \sim Poi(\lambda_2)$, and $X_1, X_2$ are independent, then $X_1 + X_2 = Poi(\lambda_1 + \lambda_2)$
Proof. 
$$
P\{X_1 + X_2 = k\} = \sum_{j = 0}^k P(X_1 = j, X_2 = k - j)
$$ 

$$
= \sum_{j = 0}^k \left(\frac{e^{-\lambda_1}\lambda_1^j}{j!}\right) \left[\frac{e^{-\lambda_2}\lambda_2^{k - j}}{(k - j)!}\right] = \frac{e^{-(\lambda_1 + \lambda_2)}}{k!}\sum_{j = 0}^k\binom{k}{j}(\lambda_1)^j(\lambda_2)^{k - j}
$$

$$
= \frac{e^{-(\lambda_1 + \lambda_2)}}{k!}(\lambda_1 + \lambda_2)^k
$$

__Definition 2.__ The Poisson process with rate $\lambda$ is the countinuous stochastic process $\{X_t\}_{t \ge 0}$.  $X_0 = 0$, and for any times $0 \le s_1 \le t_1 \le s_2 \le t_2 ... \le s_k \le t_k$, the random variable $X_t - X_s$, are independent, and have Poisson distribution with mean $\lambda(t_j - s_j)$
- $X_t \sim Poi(\lambda t), E[X_t] = \lambda t$

__Example.__ Suppose $\{X_t\}$ is a Poisson process with mean $\lambda = 2$. Find 
- $P\{X_5 = 4\}$

$$ 
X_5 = (X_1 - X_0) + (X_2 - X_1) + (X_3 - X_2) + (X_4 - X_3) + (X_5 - X_4) 
$$

$$ 
X_5 \sim Poi(10) \implies P\{X_5 = 4\} = \frac{e^{-10}\cdot 10^4}{4!}
$$

- $P\{X_3 = 4 \mid X_6 = 10\}$

$$ = \frac{P\{X_3 = 4, X_6 = 10\}}{P\{X_6 = 10\}} =\frac{P\{X_3 = 4, X_6 - X_3 = 6\}}{P\{X_6 = 10\}} = \binom{10}{4} \frac{1}{2^{10}}
$$
- Intuition: Happened 10 times, arrange 4 into first three 

__Remark.__ We can describe poisson process in terms of an arrival times. Let $\tau_0 = 0$, and let 
$$
\tau_j = \inf\{t \ge 0: X_t = j\}
$$be the time of $j$-th call 
We have $X_t = \max\{j : \tau_j \le t\}$

__Definition 3.__ A random variable $T \in [0, \infty)$ has the exponential distribution if $\forall t \ge 0$, if $T\sim \operatorname{Exp}(\lambda)$, $f_T(t)=\lambda e^{-\lambda t}, \qquad t\ge 0$
$$
P\{T \ge t\} = e^{-\lambda t}
$$

$$
E[T] = \int_{0}^{\infty} e^{-\lambda t}\lambda t = \frac{1}{\lambda}
$$

__Proposition.__ The arrival time $\tau_j - \tau_{j - 1}$, for $j = 1, 2, ...$ are i.i.d $\exp(\lambda)$
$$
P\{\tau_1 > t\} = P\{X_t = 0\} = e^{-\lambda t}
$$ 

The rest follows strong Markov property

__Example.__ Suppose $\{X_t\}$ is a poisson process with mean = 3, find 
- $E[\tau_{12}] = E[(\tau_{12} - \tau_{11}) + (\tau_{11} - \tau_{10}) + ... + \tau_1] = 4$
- $E[\tau_{12} \mid X_2 = 5] = 2 + E[\tau_7] = \frac{13}{3}$
- $E[\tau_2 \mid \tau_1 > 3]$

$$
E[(\tau_2 - \tau_1) + \tau_1 \mid \tau_1 > 3] = E[\tau_2 - \tau_1] + E[\tau_1 \mid \tau_1 > 3] = \frac13 + 3 + \frac13 = \frac{11}{3}
$$ 

