# mnmce-solutions

This repository corresponds to 3 interesting answers submitted by me as the evaluation method for a post-graduation subject called Numerical Methods and Computational Models.

## After $N$ independent and uniformly distributed random variables between 0 and 1, are sorted in non-decreasing order, what is the probability that the rth smallest value is $\leq x$?

The question corresponds to exercise 7 located on page 7 of Chapter 5 - Sorting and Searching of the book "The Art of Computer Programming - Volume 3" by Donald Ervin Knuth.

-----

We have $N$ random variables $Z$ that follow the distribution $Z \sim U[0, 1]$. In sequence notation: $\\{Z_{i}\\}_{i = 1}^{N}$.
Let's define a new random variable $Y$, which depends on $Z$ and follows the following Bernoulli distribution:

$$
Y(Z) \sim Bernoulli 
\begin{cases}
1,&if& Z\leq x\\
0,&if& Z > x
\end{cases}
$$

Note that $P(Y = 1) = P(Z \leq x) = x$ and $P(Y = 0) = P(Z > x) = 1 - x$, due to the distribution of $Z$. 
Consider the following sequence $\\{Y_{i}\\}_{i = 1}^{N}$ of zeros and ones. If we sort the sequence $\\{Z_{i}\\}_{i = 1}^{N}$ in a non-decreasing way, the sequence $\\{Y_{i}\\}_{i = 1}^{N}$ will be the number 1 appearing a few times, followed by zeros. This sequence starts to be 0 as soon as the kth value $\\{Z_{i}\\}_{i = 1}^{N}$ becomes greater than $x$.

The r-th term of the ordered $\\{Z_{i}\\}_{i = 1}^{N}$ will be less than $x$ if the sequence $\\{Y_{i}\\}_{i = 1}^{N}$ has more ones than the value of $r$. The number of ones in $\\{Y_{i}\\}_{i = 1}^{N}$ is $\sum_{i = 1}^{N} Y_{i}$.
Since all these Bernoullis are independent and identically distributed, we can use the fact that a summation of Bernoulli variables follows the Binomial distribution:

$$
\sum\{Y_{i}\}_{i = 1} ^{N} = S \sim Binomial(N, x)
$$


We are interested in computing $P(S > r )$ which is equal to

$$
P(S  > r ) = \sum_{j = r + 1}^{N}P(S = j) =\\
 \sum_{j = r + 1}^{N} \binom{N}{j} x^{j}(1 - x)^{N - j}
$$
