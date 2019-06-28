[Think Stats Chapter 3 Exercise 1](http://greenteapress.com/thinkstats2/html/thinkstats2004.html#toc31) (actual vs. biased)

>> The question first asked us to compute the distribution of the number of children reported by each family. To do that (without using the author's method), I counted the number of appearances of each value (i.e. frequency), used that to compute the probability of each value by dividing by the total number of responses, and plotted these probabilities as a bar chart.

```python
resp = nsfg.ReadFemResp()
num_kids = resp.numkdhh

from collections import Counter
actual_counts = dict(Counter(num_kids))
actual_prob = {}
for key, val in actual_counts.items():
    actual_prob[key] = val / len(num_kids)
actual_prob

from matplotlib import pyplot as plt
bar1 = plt.bar(actual_prob.keys(), actual_prob.values())
plt.xlabel('Number of children in family')
plt.ylabel('PMF')
plt.savefig('barplot1.png')
```

> > This produced the distribution shown in the bar plot:

![barplot image 1](https://github.com/peterilhardt/dsp/tree/master/lessons/statistics/barplot1.png)



> > It then asked us to compute a biased distribution that would result from surveying the children themselves. For this, I multiplied each count of the number of children reported by the number of children reported, since children in the same family would report the same number of children in that family, and those values would be disproportionately represented. Families with zero children would not be counted at all. I then computed the probabilities like before and generated the distribution shown:

![barplot image 2](https://github.com/peterilhardt/dsp/tree/master/lessons/statistics/barplot2.png)

> > The code for this was:

```python
bias_counts = {}
bias_prob = {}
for key, val in actual_counts.items():
    bias_counts[key] = key * val
total = sum(bias_counts.values())
for key, val in bias_counts.items():
    bias_prob[key] = val / total
bias_prob

bar2 = plt.bar(bias_prob.keys(), bias_prob.values())
plt.xlabel('Number of children in family')
plt.ylabel('Biased PMF')
plt.savefig('barplot2.png')
```

> > Finally, the problem asked for the mean of each distribution, which was 1.02 for the unbiased count and 2.46 for the biased count.

```python
print(num_kids.mean())
bias_kids = num_kids**2
print(bias_kids.mean())
```
