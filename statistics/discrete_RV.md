# Overview
For a random variable $X$, 
- CDF

$$\mathrm{F}(x):=\mathrm{P}(X \leq x)$$


- PMF\
if $p(x) \geq 0$ and for all events $A$
$$\mathrm{P}(X \in A)=\sum_{x \in A} p(x)$$

- EV

$$
\mathrm{E}[X]:=\sum_i x_i p\left(x_i\right)
$$

- Variance

$$
\begin{aligned}
\operatorname{Var}(X) & :=\mathrm{E}\left[(X-\mathrm{E}[X])^2\right] \\
& =\mathrm{E}\left[X^2\right]-\mathrm{E}[X]^2
\end{aligned}
$$

## Binomial Distribution

### :small_blue_diamond: Definition
The binomial distribution is a discrete probability distribution that describes the number of successes in a fixed number of independent trials, where each trial has the same probability of success. It is denoted by $B(n,p)$, where $n$ is the number of trials and $p$ is the probability of success in each trial. 

- PMF

$$
\mathrm{P}(X=r)=\left(\begin{array}{c}
n \\
r
\end{array}\right) p^r(1-p)^{n-r}
$$

where $X$ is the random variable representing the number of successes in $n$ trials, $k$ is the number of successes, and $\binom{n}{k}$ is the binomial coefficient, which represents the number of ways to choose $k$ successes out of $n$ trials. 

- EV

$$
\mathrm{E}[X]=np
$$

- Variance

$$
Var(X) = np(1-p)
$$

### :small_blue_diamond: Sum of Binomials
Binomial RV is sum of Bernoulli RV's. \
Let $X_1...X_n$ be independent $Bernoulli(p)$ RV's, then $X = X_1 + ...+ X_n$ has $Binomial(n,p)$ distribution. \
Suppose $X \sim \operatorname{Bin}(n, p)$, $Y \sim \operatorname{Bin}(m, p)$. Define $Z=X+Y$. 
Then 

$$
p_z(x=k)=\left(\begin{array}{c}
n+m \\
k
\end{array}\right) p^k(1-p)^{n+m-k}
$$

That is, $Z \sim \operatorname{Bin}(n+m, p)$.

### :small_blue_diamond: Examples

#### :notebook: Fund Manager Performance

#### Suppose a fund manager outperforms the market in a given year with probability $1/2$ and she underperforms the market with probability $1/2$. She has a track record of $10$ years and has outperformed the market in $8$ of the $10$ years. Moreover, performance in any one year is independent of performance in other years. How likely is a track record exactly as this?

Let $A$ be the event that the fund manager outperforms the market in a given year, and let $B$ be the event that she underperforms the market. Then we know that $P(A) = 1/2$ and $P(B) = 1/2$. Let $X$ be the number of years in which the fund manager outperforms the market in her 10-year track record.

We want to find $P(X = 8)$, the probability that the fund manager outperforms the market in 8 out of 10 years. We can use the binomial distribution to compute this probability:

$$
P(X=8)=\left(\begin{array}{c}10 \\ 8\end{array}\right)\left(\frac{1}{2}\right)^8\left(\frac{1}{2}\right)^2=45 \cdot \frac{1}{1024}=\frac{45}{1024}
$$

Therefore, the probability of having a track record as good as this is $\frac{45}{1024}$, which is approximately 4.39%.

#### How likely is a track record as good as this?

$$
\mathrm{P}(X \geq 8)=\sum_{r=8}^n\left(\begin{array}{c}n \\ r\end{array}\right) p^r(1-p)^{n-r} = \left(\begin{array}{c}10 \\ 8\end{array}\right)\left(\frac{1}{2}\right)^8\left(\frac{1}{2}\right)^2 + \left(\begin{array}{c}10 \\ 9\end{array}\right)\left(\frac{1}{2}\right)^9\left(\frac{1}{2}\right)^1 + \left(\begin{array}{c}{10} \\ {10}\end{array}\right)\left(\frac{1}{2}\right)^{10}\left(\frac{1}{2}\right)^0 $$

, which is approximately 5.47%.

#### Suppose there are $M$ fund managers? How well should the best one do over the 10-year period if none of them had any skill?
Assuming none of the fund managers have any skill, their performance will be determined purely by chance. Let's suppose that each manager has a 50/50 chance of outperforming the market in any given year, independent of all other managers.

The probability that at least one manager outperforms the market in any given year is $1/2$, and the probability that none of them outperform the market is also $1/2$. Therefore, the probability that all $M$ managers underperform the market in a given year is $(1/2)^M$.

The probability that at least one manager outperforms the market **in all 10 years** is $(1/2)^{10M}$, and the probability that none of them outperform the market in all 10 years is $(1/2)^{10M}$. Therefore, the probability that the best fund manager outperforms the market in at least one of the 10 years is $1-(1/2)^{10M}$.

Suppose we want to find the minimum performance of the best fund manager over the 10-year period such that their outperformance can be attributed purely to chance. We can solve for this value by setting the probability of at least one fund manager outperforming the market equal to the significance level $\alpha$ (say, $\alpha = 0.05$ for a 5% significance level). That is,

$1 - (1/2)^{10M} = \alpha$.

Solving for $M$, $M = \frac{log(1-\alpha)}{10log(2)}$

For example, if we choose $\alpha = 0.05$, then $M \approx 5.79$. This means that if there are fewer than 6 fund managers, we can expect the best one to outperform the market at least once purely by chance. If there are more than 6 fund managers, then we would expect at least one of them to outperform the market in all 10 years simply due to chance.

In conclusion, if none of the fund managers have any skill, then the best-performing manager would need to achieve a performance that is significantly better than chance (as determined by the number of managers) in order to demonstrate any real skill.

#### :notebook: Multiple Choice Guess
#### Suppose you take an exam that contains 20 multiple choice questions. Each question has 4 possible options. You know the answer to 10 questions, but for the other 10 questions, you choose answers randomly. Each question worths a point. Let $X$ be your score on the exam. What is $P(X \gt 15)$?

$$ X = 10 + Y $$

$$
\begin{aligned}
\begin{equation}
P_Y(y)=\left(\begin{array}{c}
10 \\
y
\end{array}\right)\left(\frac{1}{4}\right)^y\left(\frac{3}{4}\right)^{10-y}
\end{equation}
\end{aligned}
$$


Want $P_X(k)$ where $k=15, 16, ..., 20$.

$$
\begin{aligned}
P(X=k) &= P(10+Y=k) \\
&= P(Y=k-10)\\
&= \left(\begin{array}{c}
10 \\
k-10
\end{array}\right)\left(\frac{1}{4}\right)^{k-10}\left(\frac{3}{4}\right)^{20-k} \nonumber
\end{aligned}
$$

## Poisson Distribution
### :small_blue_diamond: Definition

The Poisson distribution is a discrete probability distribution that describes the probability of a given number of events occurring in a fixed interval of time or space, given that these events occur at a constant average rate and independently of each other. 

- PMF

$$
P(X=k)=\frac{\lambda^{k} e^{-\lambda}}{k !}
$$

where $X$ is the random variable representing the number of events in the interval, $k$ is a non-negative integer, $e$ is the mathematical constant approximately equal to 2.71828

- EV

$$
\begin{aligned}
E(X) &= \sum_{k=0}^{\infty} k P(X=k) \
&= \sum_{k=0}^{\infty} k \frac{\lambda^k}{k!} e^{-\lambda} \
&= e^{-\lambda} \sum_{k=1}^{\infty} \frac{\lambda^k}{(k-1)!} \
&= e^{-\lambda} \lambda \sum_{j=0}^{\infty} \frac{\lambda^j}{j!} \quad \text{ (substituting } j=k-1 \text{)} \
&= e^{-\lambda} \lambda e^{\lambda} \
&= \lambda
\end{aligned}
$$

This result comes from the power series expansion of the exponential function: $e^x = \sum_{j=0}^{\infty} \frac{x^j}{j!}$ in which we substitute $x = \lambda$.

> :information_source: The power series expansion of the exponential function\
> Intuitively, the power series expansion of the exponential function can be thought of as an infinite sum of terms, where each term is a power of the variable x divided by the factorial of the exponent. The larger the exponent, the smaller the contribution of each term, so the sum converges to the exponential function as the number of terms increases.\
> In LaTeX form, the power series expansion of the exponential function can be written as: 
> 
> $$
> e^x = \sum_{n=0}^{\infty} \frac{x^n}{n!}
> $$
> 
> Here, the summation symbol $\sum$ indicates that we are adding up all the terms from $n=0$ to infinity. The variable $x$ is raised to increasingly higher powers, starting from $x^0$ in the first term, $x^1$ in the second term, $x^2$ in the third term, and so on. Each term is divided by the factorial of its exponent, which ensures that the sum converges to the exponential function as the number of terms increases.

- Variance

$$
\begin{aligned}
Var(X) &= E(X^2) - [E(X)]^2 \\
&= \sum_{k=0}^{\infty} k^2 P(X=k) - \lambda^2 \\
&= \sum_{k=0}^{\infty} k^2 \frac{\lambda^k}{k!} e^{-\lambda} - \lambda^2 \\
&= e^{-\lambda} \sum_{k=1}^{\infty} k \frac{\lambda^k}{(k-1)!} - \lambda^2 \\
&= e^{-\lambda} \lambda \sum_{j=0}^{\infty} (j+1) \frac{\lambda^{j}}{j!} - \lambda^2 \quad \text{ (substituting } j=k-1 \text{)} \\
&= e^{-\lambda} \lambda \left[\sum_{j=0}^{\infty} j \frac{\lambda^{j}}{j!} + \sum_{j=0}^{\infty} \frac{\lambda^{j}}{j!}\right] - \lambda^2 \\
&= e^{-\lambda} \lambda \left[\sum_{j=1}^{\infty} \frac{\lambda^{j-1}}{(j-1)!} + e^{\lambda}\right] - \lambda^2 \quad \text{ (splitting first term into j=0 and j>0)} \\
&= e^{-\lambda} \lambda (\lambda e^{\lambda} + e^{\lambda}) - \lambda^2 \\
&= \lambda e^{-\lambda} e^{\lambda} (\lambda + 1) - \lambda^2 \\
&= \lambda (\lambda + 1) - \lambda^2 \\
&= \lambda
\end{aligned}
$$


### :small_blue_diamond: Poisson as an approximation of Binomial
The Poisson distribution can be used as an approximation of the binomial distribution under certain conditions. Specifically, when the number of trials in a binomial distribution is very large and the probability of success is very small, the resulting distribution can be approximated by a Poisson distribution with a mean equal to the product of the number of trials and the probability of success.

This is because the Poisson distribution is often used to model rare events, while the binomial distribution models the number of successes in a fixed number of trials. When the number of trials is large and the probability of success is small, the number of successes is also likely to be small, making the event rare. In this case, the Poisson distribution can be used to approximate the binomial distribution.

In the case of a binomial distribution with $n$ trials and probability of success $p$, the mean is equal to $np$. If $n$ is very large and $p$ is very small, then $np$ is still relatively small and can be used as the mean of the Poisson distribution.

Thus, the Poisson distribution can be used as an approximation of the binomial distribution when $np \le 10$ and $p \le 0.1$.

### :small_blue_diamond: Sum of Poissons
Suppose $X \sim \operatorname{Poisson}(\alpha)$, $Y \sim \operatorname{Poisson}(\beta)$. Define $Z=X+Y$. then $Z \sim \operatorname{Poisson}(\alpha + \beta)$.

### :small_blue_diamond: Poisson Distribution is memoryless

#### :notebook: Bus Waiting

Suppose that buses arrive at the bus stop, on average, once every 10 minutes. We can model the time between bus arrivals using an exponential distribution with parameter $\lambda = 1/10$ (since the expected time between bus arrivals is 10 minutes).

Now, suppose that a person arrives at the bus stop and has been waiting for 5 minutes already. What is the probability that the next bus arrives within the next 3 minutes?

Since the Poisson process is memoryless, the probability of the next bus arriving within the next 3 minutes is the same as if the person had just arrived at the bus stop and was waiting for the first bus. This is because the Poisson process assumes that events occur independently and randomly over time, and the probability of an event occurring in a fixed time interval is determined solely by the expected rate of occurrence of the event.

Therefore, the probability of the next bus arriving within the next 3 minutes is given by the probability that a bus arrives within the first 3 minutes of waiting. This can be calculated using the cumulative distribution function of the exponential distribution:

$$
P(X \leq 3)=\int_0^3 \lambda e^{-\lambda x} d x=1-e^{-\lambda 3} \approx 0.259
$$

So, the probability that the next bus arrives within the next 3 minutes is approximately 0.259, regardless of how long the person has already been waiting. This is an example of the memoryless property of the Poisson process.

### :small_blue_diamond: Examples

#### :notebook: Email Receipt 

#### If 0.2 email is received per minute on average. What is the probability that no email is received in an inverval of 5 minutes?

$$
\lambda = 0.2 * 5 = 1 \Rightarrow P(X=0)=\frac{1^{0} e^{-1}}{0 !} \approx 0.3679
$$

#### What is the probability that there're more than 3 emails within 10 minutes?

$$
\lambda = 0.2 * 10 = 2 \Rightarrow P(X \gt 3)= 1 - (\frac{2^{0} e^{-2}}{0 !} + \frac{2^{1} e^{-2}}{1 !} + \frac{2^{2} e^{-2}}{2 !} + \frac{2^{3} e^{-2}}{3 !}) 
$$

## Geometric Distribution

### :small_blue_diamond: Definition
The geometric distribution is a probability distribution that models the number of trials needed to obtain the first success in a sequence of independent Bernoulli trials, where a "success" is an event with probability $p$ and a "failure" is an event with probability $(1-p)$, and the trials are repeated until the first success occurs.

- PMF

$$
P(X = k) = (1-p)^{k-1} * p
$$

where $X$ is the number of trials needed to obtain the first success, $k$ is a positive integer, and $p$ is the probability of success in each trial.\
In other words, if we repeatedly perform independent trials, each with probability $p$ of success, then the geometric distribution gives the probability that we will obtain the first success on the $k$-th trial.

- EV

$$
\mathrm{E}[X]= \frac{1}{p}
$$

where $X$ is the random variable representing the number of trials needed to obtain the first success, and $p$ is the probability of success in each trial.

Intuitively, the expected value represents the average number of trials required to obtain the first success. This makes sense since the more likely we are to succeed in each trial (i.e., the higher the value of $p$), the fewer trials we would expect to need to obtain the first success.

- Variance

$$
Var(X) = \frac{1-p}{p^2}
$$

### :small_blue_diamond: Geometric Distribution is memoryless
The geometric distribution is memoryless, which means that the probability of getting a success on the next trial does not depend on how many failures have been observed previously. This might seem a bit counterintuitive at first, but one way to think about it is to consider the following scenario:

Suppose you are flipping a fair coin, and you want to know the probability of getting heads on the next flip, given that the previous three flips were tails. Since the coin is fair, the probability of getting heads on any given flip is 0.5, regardless of what happened on previous flips. Therefore, the probability of getting heads on the next flip is still 0.5, even though you have just observed three consecutive tails.

Similarly, in the geometric distribution, the probability of getting a success on any given trial is fixed at $p$, regardless of how many failures have been observed previously. This is why the distribution is memoryless - the probability of success on the next trial does not depend on the outcome of previous trials. For example, if the probability of success is $p = 0.2$, then the probability of getting a success on the first trial is 0.2, the probability of getting a success on the second trial (given that the first trial was a failure) is still 0.2, and so on. This makes the geometric distribution a very simple and intuitive model for certain kinds of random processes.

### :small_blue_diamond: Examples

#### :notebook: Coin Tossing
#### Given a fair coin, what is the total number of coin tosses until we observe the first head?
The number of coin tosses until we observe the first head follows a geometric distribution with parameter $p=0.5$ (since we have a fair coin).

The expected value of a geometric distribution with parameter $p$ is $E(X) = \frac{1}{p}$. Therefore, in this case, the expected number of coin tosses until we observe the first head is:

$$
\mathrm{E}[X]= \frac{1}{0.5} = 2
$$

So we would expect to flip the coin twice, on average, before observing the first head. Note that this is just an average - it is possible to observe the first head on the first flip, or to have to flip the coin many times before observing the first head.
