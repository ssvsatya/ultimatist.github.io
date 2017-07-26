---
layout: post
title: Finding Your Functional Form
---

As a data science instructor at [Metis](https://thisismetis.com), I'm not surprised how motivated and eager my students are to dive into [Machine Learning](https://en.wikipedia.org/wiki/Machine_learning). After all, data munging and [ETL](https://en.wikipedia.org/wiki/Extract,_transform,_load) aren't what get me fired up to tackle a new dataset either. For a host of reasons, including prior exposure and interpretability, our curriculum introduces linear regression as the first of many ML methodologies. And, invariably, someone will question what there is to learn that wasn't already covered in the 11th grade exposition on \$$ y = mx + b $$

Box-Cox Normality Plot. Purpose: Find transformation to normalize data. Many statistical tests and intervals are based on the assumption of normality. The assumption of normality often leads to tests that are simple, mathematically tractable, and powerful compared to tests that do not make the normality assumption.

Although it's quite tempting to jump straight into a statistical test for normality of our data, it's critical to get to know our data first by building a visualization first, and checking for these possible red flags:

- Excess skew
  - Data appears lopsided, one tail much longer than another
![skew](https://upload.wikimedia.org/wikipedia/commons/thumb/f/f8/Negative_and_positive_skew_diagrams_%28English%29.svg/446px-Negative_and_positive_skew_diagrams_%28English%29.svg.png)

- Extreme kurtosis
  - Tall and thin curve, or short and fat curve
![kurtosis](http://schaal15.blog.sbc.edu/files/2014/11/kurtosis1.jpg)
_Credit: whatilearned.wikia.com_


- Multimodal distribution
  - More than one mode, or peak
![Multimodal](https://prateekvjoshi.files.wordpress.com/2013/06/multimodal.jpg)


Functional Form | Equation (One Feature) | Interpretation
-----|-------|---------
Linear|ok|B1 unit change in Y per unit change in X
Lin-Log | | B1/100 unit change in Y per 1% change in X
Log-Lin || B1*100 percent change in Y per unit change in X
Log-Log (Double-Log)|| B1% change in Y per % change in X (B1 is called _elasticity_ of Y for X)
Polynomial || B1 + 2B2X change in Y per unit change in X


![Example of Log2-Lin functional form](https://upload.wikimedia.org/wikipedia/commons/f/f8/Influenza-2009-cases-logarithmic.png)

In the above example, we have a linear time progression, but an exponential growth in H1N1 cases. To simulate linearity, a logarithm transformation with base 2 on Y gives us the best results. So our model's functional form is Log2-Lin.
