# Stats

 

## Chebyshev's Inequality

![[eq2]](https://www.statlect.com/images/Chebyshev-inequality__6.png)

P (| random variable - mean| >= K ) <= variance / K^2

> Suppose we extract an individual at random from a population whose members have an average income of $40,000, with a standard deviation of $20,000. What is the probability of extracting an individual whose income is either less than $10,000 or greater than $70,000? In the absence of more information about the distribution of income, we cannot compute this probability exactly. However, we can use Chebyshev's inequality to compute an upper bound to it. If ![X](https://www.statlect.com/s.gif) denotes income, then ![X](https://www.statlect.com/s.gif) is less than $10,000 or greater than $70,000 if and only if

P (| random variable - mean| >= K ) <= variance / K^2

K = 30k; since 10k + K = mean; mean + K = 70k 

​							<= 20k ^2 / 30k^2 

Therefore, the probability of extracting an individual outside the income range $10,000-$70,000 is less than 4/9 



## Hoeffding's lemma


$$
E[ e^{\lambda X}]
$$



