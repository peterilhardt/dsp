[Think Stats Chapter 5 Exercise 1](http://greenteapress.com/thinkstats2/html/thinkstats2006.html#toc50) (blue men)

>> This question asks for the percentage of men who would meet the height requirements to be in Blue Man Group (must be between 5'10'' and 6'1"), given that male heights approximately follow a normal distribution with mean = 178 cm and standard deviation = 7.7 cm. To answer this question, we need to generate a normal distribution with those parameters and estimate the proportion from the CDF. This is done with `scipy.stats.norm`: 

```python
import scipy.stats as stats
mu = 178
sigma = 7.7
dist = stats.norm(loc = mu, scale = sigma)
```

The proportion of men in this range is simply the cumulative distribution estimate for the max value (6'1" converted to cm) minus the cumulative distribution estimate for the min value (5'10" converted to cm):

```python
dist.cdf(73*2.54) - dist.cdf(70*2.54)   #2.54 cm per inch
```

This comes out to about **34.27%**.
