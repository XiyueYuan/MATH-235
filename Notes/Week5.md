### Continuous Time Markov Chain 
__Definition 1.__ Transition rates 
$$
\alpha(x, y) \ge 0
$$
- the rate of jumping from $x$ to $y$
$$
\alpha(x, y) = 2 = \lambda_1, \quad \alpha(x, z) = 3 = \lambda_2
$$

Then 
$$
\alpha(x) = 5, \quad T_x \sim Exp(5), \quad E[T_x] = \frac15
$$

$$
T_{\text{total}} = T_x, \quad P(T_y < T_z) = \int_{0}^{\infty}P(T_z > t)f_{T_y}(t)dt = \frac{\lambda_2}{\lambda_1 + \lambda_2}
$$

__Property__
$$
T \sim exp(\alpha(x)), \quad \alpha(x) = \sum_{y \in S, y \neq x} \alpha(x, y), \quad P[X_T = y] = \frac{\alpha(x, y)}{\alpha(x)}
$$

In discrete Markov Chain 
$$
p(x, y) = P(X_{n + 1} = y \mid X_n = x)
$$

In Continuous Time Markov Chain:
$$
p_t(x, y) = P(X_t = y \mid X_0 = x)
$$

For a very small time $\epsilon$, if you are currently at $x$, then 
$$
P(X_{t + \epsilon} = y \mid X_t = x) \approx \alpha(x, y)\epsilon, \quad \epsilon \to 0
$$

Proof
$$
T_y \sim Exp(\alpha(x, y))
$$

So, 
$$
P(T_y < \epsilon) = 1 - e^{-\alpha(x, y) \epsilon}
$$

For very small $\epsilon$, by Taylor Expansion
$$
1 - e^{-\alpha(x, y) \epsilon} \approx \alpha(x, y)\epsilon
$$

$$
\frac{d}{dt}p_t(x,y)=\sum_{z\neq y}\alpha(z,y)p_t(x,z)-\alpha(y)p_t(x,y)
$$

Generator Matrix: 
For $x \neq y$, 
$$
A(x, y) = \alpha(x, y)
$$

For diagonal: 
$$
A(x, x) = -\alpha(x)
$$

Rows sum to 0
$$
\sum_y A(x,y)=0
$$

__Example__
$$
\alpha(A, B) = 2, \quad P(A \to B) = 2\epsilon
$$

$$
\alpha(A, C) = 8, \quad P(A \to C) = 8\epsilon
$$

Total rate leaving A
$$
\alpha(A) = 2 + 8 = 10
$$

So the probabililty of not leaving A is 
$$
1 - 10\epsilon
$$

Generator matrix stores all the instantaneous rate, row A:
$$
[-10, 2, 8] 
$$

We can get. the approximate one-step probability
$$
[P(A \to A), P(A \to B), P(A \to C)] = [1-10\varepsilon,\ 2\varepsilon,\ 8\varepsilon]
$$

__Example__
A machine has two states: 
- W = Working
- B = Broken

The machine breaks at rate 0.4 per day.
The machine is repaired at rate 1.6 per day.

$$
\alpha(W, B) = 0.4, \quad \alpha(B, W) = 1.6
$$

- Now we can derive the generator matrix
$$
A = \begin{bmatrix}
-0.4,& 0.4 \\ 
1.6, &-1.6
\end{bmatrix}
$$

- The expected time the machine stays working before breaking is $\frac{1}{0.4} = 2.5$
  
- For tiny $\epsilon = 0.1$ day,
$$
P(W \to B) = 0.4 \epsilon = 0.04, \quad P(W \to W) = 1 - 0.4\epsilon = 0.96
$$

Notice above are approximation, real formula is 
$$
P(W \to B) = 1 - e^{-0.4\epsilon}
$$

__Stationary Distribution__
- $\pi A = 0$
- $\sum_{x \in S}\pi_x = 1$