[Think Stats Chapter 2 Exercise 4](http://greenteapress.com/thinkstats2/html/thinkstats2003.html#toc24) (Cohen's d)

>> The question asks us to use Cohen's d to compare the weights of first babies (first in birth order) to non-first babies. To do this, I wrote a function `cohend` to compute the Cohen's d statistic for effect size between two input groups, and calculated this value for the *totalwgt_lb* variable in each group:

```python
def cohend(group1, group2):
    pooled_s = np.sqrt(((group1.var()*(len(group1) - 1)) + (group2.var()*(len(group2) - 1))) 
                       / (len(group1) + len(group2) - 2))
    return (group1.mean() - group2.mean()) / pooled_s

print(firsts['totalwgt_lb'].mean() - others['totalwgt_lb'].mean())
print(cohend(firsts['totalwgt_lb'], others['totalwgt_lb']))
print(cohend(firsts['prglngth'], others['prglngth']))
```

> The difference in mean weights between first babies and others is -0.12, suggesting first babies tend to be about 2 ounces lighter than other babies on average. The Cohen's d for this comparison is -0.089, which is about a three times greater effect size (in magnitude) than that for the comparison of pregnancy lengths for these groups (Cohen's d = 0.029), but is still pretty small. I think this effect size would not be considered to have practical significance. 
