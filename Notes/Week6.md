### Conditional Expectation 
Let $x$ and $y$ be random variables taking values on countable states $S, T \in \mathbb R$
$$
f(x, y) = P[X = x, y = y]
$$

Then 
$$
E[X \mid Y] = \frac{\sum_{x \in S}xf(x, y)}{\sum_{x \in S}f(x, y)}
$$

__Def.__ Let $X, Y$ be random variables with $X \in \mathbb R$, $E[|X|] < \infty$. The conditional expectation $E[X \mid Y]$ is the unique random variable satisfying 
- $E[X \mid Y]$ is a function of $Y$
- If $F(Y)$ is any function of $y$ with $E[|F(Y)|] < \infty$, 

Then $E[E[X \mid Y]F(Y)] = E[XF(Y)]$

__Properties of conditional expectation:__
- Consider a sequence of random variables $\{Y_n\}_{n \in \mathbb N}$

__Def.__ We write $\mathcal F_n$ for the information contained in $Y_0, Y_1, ... Y_n$

__Def.__ $E[X \mid \mathcal F_n]$ is the unique random variable satisfying 
- $E[X \mid \mathcal F_n]$ is $\mathcal F_n$ measurable
- We say that a random varaible $Z$ is $\mathcal F_n$-measurable if it is a function of $Y_0, ..., Y_n$
- If $Z$ is $\mathcal F_n$-measurable, then 
$$
E[XZ] = E[E[X \mid \mathcal F_n]Z]
$$

__Prop.__ If $X_1, X_2$ are random varaibles and $a, b \in \mathbb R$
$$
E[aX_1 + bX_2 \mid \mathcal F_n] = aE[X_1 \mid \mathcal F_n] + bE[X_2 \mid \mathcal F_n]
$$

__Prop.__ If $X$ is $\mathcal F_n$ measurable, then 
$$
E[X \mid \mathcal F_n] = E[X]
$$

__Prop.__ If $X$ is independent from $\mathcal F_n$ then $E[X \mid \mathcal F_n] = E[X]$

__Prop.__ $E[E[X \mid \mathcal F_n]] = E[X]$

__Prop.__ Tower Property
$$
E[E[X \mid \mathcal F_n] \mid \mathcal F_m] = E[X \mid \mathcal F_m]
$$


### Optional Stopping Theorem (OST)
