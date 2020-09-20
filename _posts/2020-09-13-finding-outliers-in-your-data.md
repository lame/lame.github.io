---
title: Finding Outliers in Your Data
layout: post
date: '2020-09-14 09:28:57'
tag: data_insights
---

In this first post, we're going to look at some techniques to determine if your
data has outliers present. We're going to go through this exercise in R
(for the stats folks out there)!


```R
rm(list = ls())
library(outliers)
library(ggplot2)
library(mosaic)
library(stats)
set.seed(1)
```


```R
data(package = .packages(all.available = TRUE))
```


```R
data(gold, package='forecast')
plot.ts(gold, main = "Gold Prices Data")
favstats(gold)
```


<table>
<caption>A data.frame: 1 × 9</caption>
<thead>
	<tr><th></th><th scope=col>min</th><th scope=col>Q1</th><th scope=col>median</th><th scope=col>Q3</th><th scope=col>max</th><th scope=col>mean</th><th scope=col>sd</th><th scope=col>n</th><th scope=col>missing</th></tr>
	<tr><th></th><th scope=col>&lt;dbl&gt;</th><th scope=col>&lt;dbl&gt;</th><th scope=col>&lt;dbl&gt;</th><th scope=col>&lt;dbl&gt;</th><th scope=col>&lt;dbl&gt;</th><th scope=col>&lt;dbl&gt;</th><th scope=col>&lt;dbl&gt;</th><th scope=col>&lt;int&gt;</th><th scope=col>&lt;int&gt;</th></tr>
</thead>
<tbody>
	<tr><th scope=row></th><td>285</td><td>337.6625</td><td>403.225</td><td>443.675</td><td>593.7</td><td>392.5333</td><td>56.60597</td><td>1074</td><td>34</td></tr>
</tbody>
</table>




![png](/assets/2020-09-13-finding-outliers-in-your-data/output_2_1.png)


Hmm, I guess this looks semi-normal with some skewness to the right. Just to be double sure, let's see some normal data...


```R
# A box-and-whisker plot should show any outliers clearly
df <- data.frame(Data=as.vector(gold))
ggplot(df, aes(y=Data)) + geom_boxplot()
```

![png](/assets/2020-09-13-finding-outliers-in-your-data/output_4_1.png)


That upper whisker is not indicating a clear outlier, which would be a dot past the end of the whisker, but my gut is still telling me that the spike to nearly 600 in the above timeseries plot is an outlier. One great method of finding outliers is using a grubbs test! The only problem is that the grubbs test expects the data to be normally distributed. Let's check out if our data is close to a normal distribution


As a quick asside, my use of the
[ECDF function](https://www.statisticshowto.com/empirical-distribution-function/) is
inspired by a post from [eric-mjl](http://ericmjl.com/blog/2018/7/14/ecdfs/). Join his
mailing list if you can!


```R
# What the heck does normal data look like
random_normal_data <- rnorm(100)

favstats(random_normal_data)
plot.ecdf(random_normal_data, main = 'ecdf(x) of Normally Distributed Data')
qqnorm(random_normal_data, main = 'Quantile-Quantile (QQ) plot of Normally Distributed Data')
qqline(random_normal_data, col = "red", lwd = 5)
legend("bottomright", c("Data Points", "Theoretical Normal"), fill=c("black", "red"))
```


<table>
<caption>A data.frame: 1 × 9</caption>
<thead>
	<tr><th></th><th scope=col>min</th><th scope=col>Q1</th><th scope=col>median</th><th scope=col>Q3</th><th scope=col>max</th><th scope=col>mean</th><th scope=col>sd</th><th scope=col>n</th><th scope=col>missing</th></tr>
	<tr><th></th><th scope=col>&lt;dbl&gt;</th><th scope=col>&lt;dbl&gt;</th><th scope=col>&lt;dbl&gt;</th><th scope=col>&lt;dbl&gt;</th><th scope=col>&lt;dbl&gt;</th><th scope=col>&lt;dbl&gt;</th><th scope=col>&lt;dbl&gt;</th><th scope=col>&lt;int&gt;</th><th scope=col>&lt;int&gt;</th></tr>
</thead>
<tbody>
	<tr><th scope=row></th><td>-2.786015</td><td>-0.5789328</td><td>-0.003405082</td><td>0.7091181</td><td>2.674871</td><td>0.03164366</td><td>1.081341</td><td>100</td><td>0</td></tr>
</tbody>
</table>




![png](/assets/2020-09-13-finding-outliers-in-your-data/output_6_1.png)



![png](/assets/2020-09-13-finding-outliers-in-your-data/output_6_2.png)


```R
favstats(gold)

# Does our data look normally distributed?
plot.ecdf(gold, main = 'ecdf(x) of Gold Prices Data')
qqnorm(gold, main = 'Quantile-Quantile (QQ) plot of Gold Prices Data')
qqline(gold, col = "red", lwd = 5)
legend("bottomright", c("Data Points", "Theoretical Normal"), fill=c("black", "red"))
```


<table>
<caption>A data.frame: 1 × 9</caption>
<thead>
	<tr><th></th><th scope=col>min</th><th scope=col>Q1</th><th scope=col>median</th><th scope=col>Q3</th><th scope=col>max</th><th scope=col>mean</th><th scope=col>sd</th><th scope=col>n</th><th scope=col>missing</th></tr>
	<tr><th></th><th scope=col>&lt;dbl&gt;</th><th scope=col>&lt;dbl&gt;</th><th scope=col>&lt;dbl&gt;</th><th scope=col>&lt;dbl&gt;</th><th scope=col>&lt;dbl&gt;</th><th scope=col>&lt;dbl&gt;</th><th scope=col>&lt;dbl&gt;</th><th scope=col>&lt;int&gt;</th><th scope=col>&lt;int&gt;</th></tr>
</thead>
<tbody>
	<tr><th scope=row></th><td>285</td><td>337.6625</td><td>403.225</td><td>443.675</td><td>593.7</td><td>392.5333</td><td>56.60597</td><td>1074</td><td>34</td></tr>
</tbody>
</table>




![png](/assets/2020-09-13-finding-outliers-in-your-data/output_7_1.png)



![png](/assets/2020-09-13-finding-outliers-in-your-data/output_7_2.png)


It's important to note that a grubbs test expects normality, and as the data isn't strictly normal there can be some concerns about the validity of the results.


```R
grubbs.test(gold, type = 10)
```



    	Grubbs test for one outlier

    data:  gold
    G = 3.55381, U = 0.98822, p-value = 0.1965
    alternative hypothesis: highest value 593.7 is an outlier



### Grubbs Results

So it looks like we do have an outlier, with a resonable p-value of 0.1965. The important thing here is to ask ourselves if that outlier is an error in the data, or if it is valuable data that needs to be included in our models to make them more realistic to real-world. For the purposes of this example, we're going to simply assume that there was a one-day run on gold that is not likely to occur again and is not representative of our dataset as a whole.


```R
# Let's go ahead and remove that max value we think is the outlier
new_gold <- gold[-which.max(gold)]

# Let's compare the old summary to the new summary
favstats(gold)
favstats(new_gold)

# Lastly, let's take a look at the timeseries plot again
plot.ts(new_gold, main = "Gold Prices w/o Outlier Data")
```


<table>
<caption>A data.frame: 1 × 9</caption>
<thead>
	<tr><th></th><th scope=col>min</th><th scope=col>Q1</th><th scope=col>median</th><th scope=col>Q3</th><th scope=col>max</th><th scope=col>mean</th><th scope=col>sd</th><th scope=col>n</th><th scope=col>missing</th></tr>
	<tr><th></th><th scope=col>&lt;dbl&gt;</th><th scope=col>&lt;dbl&gt;</th><th scope=col>&lt;dbl&gt;</th><th scope=col>&lt;dbl&gt;</th><th scope=col>&lt;dbl&gt;</th><th scope=col>&lt;dbl&gt;</th><th scope=col>&lt;dbl&gt;</th><th scope=col>&lt;int&gt;</th><th scope=col>&lt;int&gt;</th></tr>
</thead>
<tbody>
	<tr><th scope=row></th><td>285</td><td>337.6625</td><td>403.225</td><td>443.675</td><td>593.7</td><td>392.5333</td><td>56.60597</td><td>1074</td><td>34</td></tr>
</tbody>
</table>




<table>
<caption>A data.frame: 1 × 9</caption>
<thead>
	<tr><th></th><th scope=col>min</th><th scope=col>Q1</th><th scope=col>median</th><th scope=col>Q3</th><th scope=col>max</th><th scope=col>mean</th><th scope=col>sd</th><th scope=col>n</th><th scope=col>missing</th></tr>
	<tr><th></th><th scope=col>&lt;dbl&gt;</th><th scope=col>&lt;dbl&gt;</th><th scope=col>&lt;dbl&gt;</th><th scope=col>&lt;dbl&gt;</th><th scope=col>&lt;dbl&gt;</th><th scope=col>&lt;dbl&gt;</th><th scope=col>&lt;dbl&gt;</th><th scope=col>&lt;int&gt;</th><th scope=col>&lt;int&gt;</th></tr>
</thead>
<tbody>
	<tr><th scope=row></th><td>285</td><td>337.6</td><td>403.1</td><td>443.6</td><td>502.75</td><td>392.3459</td><td>56.29777</td><td>1073</td><td>34</td></tr>
</tbody>
</table>




![png](/assets/2020-09-13-finding-outliers-in-your-data/output_11_2.png)



```R
grubbs.test(new_gold, type = 10)
```



    	Grubbs test for one outlier

    data:  new_gold
    G = 1.96107, U = 0.99641, p-value = 1
    alternative hypothesis: highest value 502.75 is an outlier



### Findings

With the max value of the data set removed, we can see that the timeseries plot no longer includes a spike right at the top. The results from the grubbs test on the new dataset omiting the max value n olonger shows a suspected outlier at the upper threashold of the data. I'd say our work here is done!

