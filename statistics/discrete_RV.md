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

### Definition
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

### Sum of Binomials
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

### Examples

#### * Fund Manager Performance

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

#### * Multiple Choice Guess
#### Suppose you take an exam that contains 20 multiple choice questions. Each question has 4 possible options. You know the answer to 10 questions, but for the other 10 questions, you choose answers randomly. Each question worths a point. Let $X$ be your score on the exam. What is $P(X \gt 15)$?

$$
\begin{align*}
P(X = 16) &= \binom{10}{6}(0.25)^6(0.75)^4 \
P(X = 17) &= \binom{10}{7}(0.25)^7(0.75)^3 \
P(X = 18) &= \binom{10}{8}(0.25)^8(0.75)^2 \
P(X = 19) &= \binom{10}{9}(0.25)^9(0.75)^1 \
P(X = 20) &= \binom{10}{10}(0.25)^{10}(0.75)^0 \
\end{align*}
$$
