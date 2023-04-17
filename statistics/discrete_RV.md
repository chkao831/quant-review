## Binomial Distribution

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
