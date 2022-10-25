# mnmce-solutions

This repository corresponds to 3 interesting answers submitted by me as the evaluation method for a post-graduation subject called Numerical Methods and Computational Models.

## After $N$ independent and uniformly distributed random variables between 0 and 1, are sorted in non-decreasing order, what is the probability that the rth smallest value is $\leq x$?

The question corresponds to exercise 7 located on page 7 of Chapter 5 - Sorting and Searching of the book "The Art of Computer Programming - Volume 3" by Donald Ervin Knuth.

-----

We have $N$ random variables $Z$ that follow the distribution $Z \sim U[0, 1]$. In sequence notation: $\\{Z_{i}\\}_{i = 1}^{N}$.
Let's define a new random variable $Y$, which depends on $Z$ and follows the following Bernoulli distribution:

$$
Y(Z) \sim Bernoulli \begin{cases}
1,&se& Z\leq x\\
0,&se& Z > x
\end{cases}
$$
