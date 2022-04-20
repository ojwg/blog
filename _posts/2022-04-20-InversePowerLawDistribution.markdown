---
layout: default
title:  "Cluster Probability Distribution"
date:   2022-04-20 09:00:00 -0400
categories: stats 
---


## Cluster probability distribution function


We use a cluster distribution function $$\phi(\mathrm{M}) = \frac{\mathrm{A}}{\mathrm{M}} $$ where $$M$$ is the cluster mass and $$A$$ is a normalization constant.  
This means that $$\mathrm{dN} \equiv \phi(\mathrm{M})\,\mathrm{dM} = \mathrm{A}\frac{\mathrm{dM}}{\mathrm{M}} = \mathrm{A\, d\log M} $$, implying that equal intervals
in log mass contain an equal number of clusters.  Intuitivily this makes sense to me since if one has a given number of clusters N at a given M and given $$\Delta\mathrm{M}$$,
then at an order of maginude greater mass the distribution function is $$0.1$$ the value it had at M, but the equal interval in $$\log$$ M means that the new interval in mass is $$10\Delta\mathrm{M}$$, yielding the same number of clusters N as before.  Another way to see it is that a distribution function in log space
$$ \equiv \frac{\mathrm{d\,N}}{\mathrm{d\log M}} = \mathrm{M}\frac{\mathrm{d\,N}}{\mathrm{d\,M}} = \mathrm {A}$$, a constant.

## Logarithm of the probability distribution

Taking the logarithm of the probability distribution one gets $$\log \phi(\mathrm{M}) = \log\mathrm{A} - \log\mathrm{M} $$, which shows a linear decrease 
with $$\log\mathrm{M}$$.  This does not imply that the probability distribution function in log space also linearly decreases with mass.  In other words 
$$\log\phi(\mathrm{M}) \neq \frac{\mathrm{d \log(N)}}{\mathrm{d \log(M)}} = \mathrm{\frac{M}{N} \frac{dN}{dM} \equiv \frac{M}{N} \phi(M)}$$. 

The original histogram from the ipython notebook provided by Dr.Evan,
![Original Histogram]({{'/assets/images/2022/04/evan_histogram.png' | relative_url}}) 

seems to follow the shape of the logarithm of the probability distribution only because it's a reverse cumulative density plot and few bins are used.  The latter point is 
important because the distribution cuts off at log mass value of 6.7, yet the rightmost bin edge is at 7.  If the `cumulative=-1` and `density=True` directives are removed
and 20 bins used, the result for that data set is
![Modified original Histogram]({{'/assets/images/2022/04/modified_evan_histogram.png' | relative_url}}) 

which does show the uniform numbers expected when binning with log mass.  

The histograms above are for a number of clusters whose total mass is $$2\times10^9\mathrm{M}_\odot$$. This is about 100 times more mass than the population I generated in 
Cholla.  If I scale up the distribution I used in Cholla to yield an equivalent amount of mass, the histogram that results is 

![Orlando Histogram]({{'/assets/images/2022/04/orlando_histogram.png' | relative_url}}) 

which is similar to the 20 binned histogram from Dr. Evan's notebook.  If I also make this a reverse cumulative density plot with 4 bins, I get a plot much like the original.

![Relative Orlando Histogram]({{'/assets/images/2022/04/cum_orlando_histogram.png' | relative_url}}) 


The original $$ 2\times10^9\mathrm{M}_\odot$$ combined mass population was made up of $$ 2443 $$ clusters.  It seems within the ballpark to assume that a population with 100 
times less mass should have 100 times fewer clusters, or a number around $$25$$.  

---



