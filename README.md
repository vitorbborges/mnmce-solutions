# mnmce-solutions

This repository corresponds to 3 interesting answers submitted by me as the evaluation method for a post-graduation subject called Numerical Methods and Computational Models in Economics.

## Show that if each element $k$ in an 'orthogonal array' is replaced by $e^{2 \pi k i / n}$, the rows become orthogonal vectors in the usual sense (their inner product is equal to zero ).

The book defines the 'orthogonal array' mathematical structure as follows:

The string $x_1 x_2 ... x_N$ is called $n-ary$ if each element $x_j$ belongs to the set $\{0, 1, ..., n - 1\}$ of digits $n-ary$. The two strings $x_1 x_2 ... x_N$ and $y_1 y_2 ... y_N$ are said to be $orthogonal$ if the $N$ pairs $(x_j,y_j)$ are distinct for $1 \leq j \leq N$. (Consequently, two strings $n-ary$ cannot be orthogonal if their length exceeds $n^2$.) A matrix $n-ary$ with $m$ rows and $n ^2$ columns whose rows are orthogonal to each other is called 'orthogonal array' of order $n$ and depth $m$.

This abstract definition is made clearer with an example of an 'orthogonal array' of order 4 and depth 5:

![orthogonal_array](http://prorum.com/?qa=blob&qa_blobid=662566948865177969)

This abstract definition is made clearer with an example of an 'orthogonal array' of order 4 and depth 5:

|   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 0 | 0 | 0 | 0 | 1 | 1 | 1 | 1 | 2 | 2 | 2 | 2 | 3 | 3 | 3 | 3 |
| 0 | 1 | 2 | 3 | 0 | 1 | 2 | 3 | 0 | 1 | 2 | 3 | 0 | 1 | 2 | 3 |
| 0 | 1 | 2 | 3 | 3 | 2 | 1 | 0 | 1 | 0 | 3 | 2 | 2 | 3 | 0 | 1 |
| 0 | 1 | 2 | 3 | 2 | 3 | 0 | 1 | 3 | 2 | 1 | 0 | 1 | 0 | 3 | 2 |

If we apply the transformation $k = e^{2k\pi i / n}$ on all elements, the inner product of any two line vectors $\textbf{x}, \textbf{y}$ can be expressed by:

$$
\begin{split}
 \textbf{x} \cdot \textbf{y}  & = \sum_{k=1}^{n^2} e^{(\frac{2\pi i}{n} \cdot x_k)} \cdot  e^{(\frac{2\pi i}{n} \cdot y_k)}\\
& =  \sum_{k=1}^{n^2} e^{( \frac{2\pi i}{n} \cdot x_k + \frac{2\pi i}{n} \cdot y_k )} \\
& =  \sum_{k=1}^{n^2} e^{\frac{2\pi i}{n} (x_k + y_k)}
\end{split}
$$

Note that all ordered pairs $\\{ (h, j) | h,j \in \\{ 0, 1, ..., n - 1 \\} \\}$ will appear in this summation, so the order we we add them up doesn't matter, so we can write:

$$
\sum_{k=1}^{n^2} e^{\frac{2\pi i}{n} (x_k + y_k)} = \sum_{h = 0}^{n - 1} \sum_{j = 0}^{n - 1} e^{\frac{2\pi i}{n} (h + j)}
$$

From now on $e^{\frac{2\pi i}{n} } = \beta$, to make notation easier.

Let's represent this double summation as follows to improve the visualization of the problem:

$$\Rightarrow \sum_{h = 0}^{n - 1} \sum_{j = 0}^{n - 1} \beta^{(h + j)} = \\
\begin{matrix}
& j = 0 & j = 1 & j = 2 & ... & j = n-3 & j = n-2 & j = n-1 \\
h = 0 & \beta^{0} & \beta^{1} & \beta^{2} & ... & \beta^{n-3} & \beta^{n-2} & \beta^{n-1} \\
h = 1 & \beta^{1} & \beta^{2} & \beta^{3} & ... & \beta^{n-2} & \beta^{n-1} & \beta^{n}\\
h = 2 & \beta^{2} & \beta^{3} & \beta^{4} & ... & \beta^{n-1} & \beta^{n} & \beta^{n+1}\\
... & & ... & & & & ... \\
h = n-3 & \beta^{n-3} & \beta^{n-2} & \beta^{n-1} & ... & \beta^{n+n-6} & \beta^{n+n-5} & \beta^{n+n-4} \\
h = n-2 & \beta^{n-2} & \beta^{n-1} & \beta^{n} & ... & \beta^{n+n-5} & \beta^{n+n-4} & \beta^{n+n-3} \\
h = n-1 & \beta^{n-1} & \beta^{n} & \beta^{n+1} & ... & \beta^{n+n-4} & \beta^{n+n-3} & \beta^{n+n-2} \\
\end{matrix}
$$

We need to add up all the elements above, looking at the secondary diagonal note that the element $\beta^{n - 1}$ appears $n$ times, in fact this happens for all elements that are above the diagonal secondary, we can write this part of the sum as:

$$
\sum_{k = 0}^{n-1} (k + 1)\beta^k
$$

Looking now at what is below the secondary diagonal, we see that each term $\\{ \beta^{n + y} | y \in \\{ 0, 1, ..., n-2 \\} \\}$ appears $(n - z - 1)$ times, such that $z \in \\{ 0, 1, ..., n-2 \\}$, we can write this part of the sum as:

$$
\sum_{k = 0}^{n-2} (n - k - 1)\beta^{n + k}
$$


Adding these two parts together we have:

$$
\begin{align*}
\textbf x \cdot \textbf y  & = \sum_{k = 0}^{n-1} (k + 1)\beta^k + \sum_{k = 0}^{n-2} (n - k - 1)\beta^{n + k} \\
& =  \sum_{k = 0}^{n-1} (k + 1)e^{\frac{2\pi i}{n} k} + \sum_{k = 0}^{n-2} (n - k - 1)e^{\frac{2\pi i}{n}(n + k)} \\
\end{align*}
$$


Applying Euler's identity: $e^{xi} = \cos(x) + i\sin(x)$

$$
\begin{align*}
\textbf x \cdot \textbf y & = \sum_{k = 0}^{n-1} (k + 1)\left(\cos\left(k\frac{2\pi}{n}\right) + i\sin\left(k\frac{2\pi}{n}\right)\right) \\ 
& + \sum_{k = 0}^{n-2} (n - k - 1)\left(\cos\left((n + k)\frac{2\pi}{n}\right) + i\sin\left((n + k)\frac{2\pi}{n}\right)\right) \\
& = \sum_{k = 0}^{n-1} (k + 1)\cos\left(k\frac{2\pi}{n}\right) + \sum_{k = 0}^{n-2} (n - k - 1)\cos\left((n + k)\frac{2\pi}{n}\right) \\
& + i \left( \sum_{k = 0}^{n-1} (k + 1)\sin\left(k\frac{2\pi}{n}\right) + \sum_{k = 0}^{n-2} (n - k - 1)\sin\left((n + k)\frac{2\pi}{n}\right) \right)
\end{align*}
$$

Let's decompose the simplification of this expression into REAL and IMAGINARY PART, starting with the REAL PART:

$$
\begin{align*} 
& = \sum_{k = 0}^{n-1} (k + 1)\cos\left(k\frac{2\pi}{n}\right) + \sum_{k = 0}^{n-2} (n - k - 1)\cos\left((n + k)\frac{2\pi}{n}\right) \\ 
& = \sum_{k = 0}^{n-1} (k + 1)\cos\left(k\frac{2\pi}{n}\right) + \sum_{k = 0}^{n-2} (n - k - 1)\cos\left(2\pi + k\frac{2\pi}{n}\right) \\ 
 \\
& \cos(2\pi + x) = \cos(x) \\
 \\
& = \sum_{k = 0}^{n-1} (k + 1)\cos\left(k\frac{2\pi}{n}\right) + \sum_{k = 0}^{n-2} (n - k - 1)\cos\left(k\frac{2\pi}{n}\right) \\ 
& = \sum_{k = 0}^{n-2} (k + 1)\cos\left(k\frac{2\pi}{n}\right) + \sum_{k = 0}^{n-2} (n - k - 1)\cos\left(k\frac{2\pi}{n}\right) +n\cos\left((n - 1)\frac{2\pi}{n}\right) \\ 
& = \sum_{k = 0}^{n-2} \left( (k + 1)\cos\left(k\frac{2\pi}{n}\right) + (n - k - 1)\cos\left(k\frac{2\pi}{n}\right) \right) +n\cos\left((n - 1)\frac{2\pi}{n}\right) \\
& = \sum_{k = 0}^{n-2} \left( (k + 1 + n - k - 1)\cos\left(k\frac{2\pi}{n}\right) \right) + n\cos\left((n - 1)\frac{2\pi}{n}\right) \\
& = \sum_{k = 0}^{n-2} \left( n\cos\left(k\frac{2\pi}{n}\right) \right) + n\cos\left((n - 1)\frac{2\pi}{n}\right) \\
& = n\sum_{k = 0}^{n-1} \cos\left(k\frac{2\pi}{n}\right) \\
\end{align*}
$$


The same simplification can be made for the IMAGINARY PART:

$$
\begin{align*} 
& = \sum_{k = 0}^{n-1} (k + 1)\sin\left(k\frac{2\pi}{n}\right) + \sum_{k = 0}^{n-2} (n - k - 1)\sin\left((n + k)\frac{2\pi}{n}\right) \\ 
& = \sum_{k = 0}^{n-1} (k + 1)\sin\left(k\frac{2\pi}{n}\right) + \sum_{k = 0}^{n-2} (n - k - 1)\sin\left(2\pi + k\frac{2\pi}{n}\right) \\ 
 \\
& \sin(2\pi + x) = \sin(x) \\
 \\
& = \sum_{k = 0}^{n-1} (k + 1)\sin\left(k\frac{2\pi}{n}\right) + \sum_{k = 0}^{n-2} (n - k - 1)\sin\left(k\frac{2\pi}{n}\right) \\ 
& = \sum_{k = 0}^{n-2} (k + 1)\sin\left(k\frac{2\pi}{n}\right) + \sum_{k = 0}^{n-2} (n - k - 1)\sin\left(k\frac{2\pi}{n}\right) +n\sin\left((n - 1)\frac{2\pi}{n}\right) \\ 
& = \sum_{k = 0}^{n-2} \left( (k + 1)\sin\left(k\frac{2\pi}{n}\right) + (n - k - 1)\sin\left(k\frac{2\pi}{n}\right) \right) +n\sin\left((n - 1)\frac{2\pi}{n}\right) \\
& = \sum_{k = 0}^{n-2} \left( (k + 1 + n - k - 1)\sin\left(k\frac{2\pi}{n}\right) \right) + n\sin\left((n - 1)\frac{2\pi}{n}\right) \\
& = \sum_{k = 0}^{n-2} \left( n\sin\left(k\frac{2\pi}{n}\right) \right) + n\sin\left((n - 1)\frac{2\pi}{n}\right) \\
& = n\sum_{k = 0}^{n-1} \sin\left(k\frac{2\pi}{n}\right) \\
\end{align*}
$$


We can join the two parts to arrive at:

$$
\begin{align*} 
\textbf x \cdot \textbf y & = n\sum_{k = 0}^{n-1} \cos\left(k\frac{2\pi}{n}\right) + ni\sum_{k = 0}^{n-1} \sin\left(k\frac{2\pi}{n}\right) \\
& = n\sum_{k = 0}^{n-1} \left( \cos\left(k\frac{2\pi}{n}\right) + i \sin\left(k\frac{2\pi}{n}\right) \right) \\
& = n\sum_{k = 0}^{n-1} e^{i\frac{2\pi k}{n}}
\end{align*}
$$

Note that proving that $n\sum_{k = 0}^{n-1} e^{i\frac{2\pi k}{n}} = 0$ is the same thing as proving that $\ sum_{k = 0}^{n-1} e^{i\frac{2\pi k}{n}} = 0$. We will then call this sum:

$$
\begin{align*} 
S_N  & = \sum_{k = 0}^{n-1} e^{i\frac{2\pi k}{n}} \\
S_N e^{i\frac{2\pi}{n}} & = \sum_{k = 0}^{n-1} e^{i\frac{2\pi (k + 1)}{n}} \\
S_N e^{i\frac{2\pi}{n}} - S_N & = \sum_{k = 0}^{n-1} e^{i\frac{2\pi (k + 1)}{n}} - \sum_{k = 0}^{n-1} e^{i\frac{2\pi k}{n}} \\
S_N(e^{i\frac{2\pi}{n}} - 1) & = e^{i2\pi} + \sum_{k = 0}^{n-2} e^{i\frac{2\pi (k + 1)}{n}} - e^0 - \sum_{k = 1}^{n-1} e^{i\frac{2\pi k}{n}} \\
& = e^{i2\pi} - 1 + \sum_{k = 0}^{n-2} e^{i\frac{2\pi (k + 1)}{n}} - \sum_{k = 0}^{n-2} e^{i\frac{2\pi (k + 1)}{n}}\\
& = e^{i2\pi} - 1 \\
\\
\Rightarrow S_N & = \frac{(e^{i2\pi} - 1)}{(e^{i\frac{2\pi}{n}} - 1)} \\
\\
& = \frac{(\cos(2\pi) + i\sin(2\pi) - 1)}{\left( cos(\frac{2\pi}{n}) + i\sin(\frac{2\pi}{n}) - 1 \right)} \\
\\
&\cos(2\pi)  = 1 \\
&\sin(2\pi)  = 0 \\
\\
& = \frac{(1 + i0 - 1)}{\left( cos(\frac{2\pi}{n}) + i\sin(\frac{2\pi}{n}) - 1 \right)} \\
\\
& = \frac{(0)}{\left( cos(\frac{2\pi}{n}) + i\sin(\frac{2\pi}{n}) - 1 \right)} \\
\\
& = 0
\end{align*}
$$

CONCLUSION: $\textbf x \cdot \textbf y = 0$, so the rows are orthogonal.

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

Consider the following sequence: $\\{Y_{i}\\}_{i = 1}^{N}$. of zeros and ones. If we sort the sequence $\\{Z_{i}\\}_{i = 1}^{N}$ in a non-decreasing way, the sequence $\\{Y_{i}\\}_{i = 1}^{N}$ will be the number 1 appearing a few times, followed by zeros. This sequence starts to be 0 as soon as the kth value $\\{Z_{i}\\}_{i = 1}^{N}$ becomes greater than $x$.

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

In order to confirm this result, two functions were implemented in the Python language. The first repeats the experiment 10,000 times and computes the proportion of experiments in which the rth term was less than x. The second uses the functional format found.

First:

```python 

import random
import scipy

random.seed(13)

def montecarlo(N, r, x):

experiment = []
#vai guardar 1 se o r do for menor que x e 0 se r for maior.

for i in range(1000):

    values = []
    #Esta lista vai guardar os valores de Z

    for i in range(N):

        values.append(random.uniform(0, 1))
        # distribuição Uniforme

    values = sorted(values)
    #ordenar os resultados

    if values[r] <= x:

        experiment.append(1)

    else:

        experiment.append(0)

return sum(experiment) / len(experiment) #proporção

```

Second:

```python

def functional(N, r, x):

p = 0

for i in range(r + 1, N + 1):

    p += scipy.special.binom(N, i)*(x**i)*((1 - x)**(N - i))

return p
```

To evaluate the result, we will calculate the average error between the brute force implementation and the functional format found.

```python
def result_efficiency():

results_1= [] #resultados de força bruta
results_2 = [] #resultados do formato funcional

for i in range(1000):

    randints = [random.randint(0, 1000), random.randint(0, 1000)]
    #sortear dois números

    N = max(randints) #o maior número é N
    r = min(randints) # o menor número é r
    x = random.uniform(0, 1)

    results_1.append(montecarlo(N, r, x))
    results_2.append(functional(N, r, x))
    #guardar os resultados

abserror_sum = [abs(z) for z in (np.array(results_1) - np.array(results_2))]
#erro absoluto
erro_medio = sum(abserror_sum)/len(abserror_sum)
#erro medio

return round(erro_medio, 5)
```

The absolute mean error found was 0.00205.
