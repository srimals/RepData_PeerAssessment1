# Reproducible Research: Peer Assessment 1


## Loading and preprocessing the data

Show any code that is needed to

1. Load the data (i.e. read.csv())


```r
library(data.table)

activity <- read.csv("activity.csv")
activity <- na.omit(activity)

actData <- data.table(activity)
```

2. Process/transform the data (if necessary) into a format suitable for your analysis



```r
actData <- actData[,steps:=as.numeric(steps)]
actData <- actData[,date :=as.Date(date)]
```


## What is mean total number of steps taken per day?

For this part of the assignment, you can ignore the missing values in the dataset.

1. Calculate the total number of steps taken per day


```r
plotdata <- actData[,sum(steps), by=date]
setnames(plotdata, c("date","V1"), c("Date","TotalSteps"))
```

2. If you do not understand the difference between a histogram and a barplot, research the difference between them. Make a histogram of the total number of steps taken each day


```r
hist(plotdata$TotalSteps, main="Total steps taken by daily", xlab="steps taken", 
     ylab="frequency", breaks=15, col="blue")
```

![](PA1_template_files/figure-html/GenerateHistogram-1.png) 

3. Calculate and report the mean and median of the total number of steps taken per day

Average steps taken per day
---------------------------

```r
mean(plotdata$TotalSteps)
```

```
## [1] 10766.19
```
Median
------


```r
median(plotdata$TotalSteps)
```

```
## [1] 10765
```




## What is the average daily activity pattern?



## Imputing missing values



## Are there differences in activity patterns between weekdays and weekends?

## end of story.
