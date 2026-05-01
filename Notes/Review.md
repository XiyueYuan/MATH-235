1. Branching process 
$$
\phi(s) = s
$$
Describes the probability of extinction __eventually__
To get the probability of extinction after $n$th generation, we have $P(X_n) = \phi(\phi^{n -1}(0))$
 example:
$$
\phi(s) = 0.2 + 0.5s + 0.3s^2
$$

$$
P(X_1 = 0) = \phi(0) = 0.2
$$

$$
P(X_2 = 0) = \phi(\phi(0)) = \phi(0.2) = 0.2 + 0.5 \times 0.2 + 0.3 \times (0.2)^2 = 0.312
$$