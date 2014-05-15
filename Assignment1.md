Reproductible Research Course  at coursera : First Assigment
========================================================

# Data summary


```r
# first we clear everything
rm(list = ls())
# Home dir
setwd("C:/Chris/Gremaq2014/Coursera/RR/progs")
# My Packages
library(xtable)
library(KernSmooth)
```

```
## KernSmooth 2.23 loaded
## Copyright M. P. Wand 1997-2009
```

```r
library(ggplot2)

# Stet global option
opts_chunk$set(ECHO = TRUE)
```

First we read the data

```r
data <- read.csv("../Data/activity.csv")
```


The data consists of two months of data from <b> a unique anonymous individual </b> collected during the months of October and November, 2012 and include the number of steps taken in 5 minute intervals each day. The data file is named  acitvity.csv and can be downloaded from the coursera Webpage. We have a sample of  <b>17568 </b> observations and <b>3</b> variables.

# Data analysis 
The mean total number of steps taken per day is just something we could represent over time but we need to do some calculation first


```r
data$date <- as.factor(data$date)
data$steps <- as.numeric(data$steps)


data$total.steps = tapply(data$steps, data$date, sum)  #apply the mean function to count steps  each date
data$unique.date = tapply(data$date, data$date, unique)
attach(data)
```




```r

hist(total.steps, freq = FALSE, nclass = 13)
```

![plot of chunk unnamed-chunk-4](figure/unnamed-chunk-4.png) 


On this sample, we observe that the mean total number of steps taken per day is 
1.0766 &times; 10<sup>4</sup>  (median =  1.0765 &times; 10<sup>4</sup>  ).



```r
plot(unique.date, total.steps, type = "l", ylab = "Total Steps/day")
```

![plot of chunk unnamed-chunk-5](figure/unnamed-chunk-5.png) 



