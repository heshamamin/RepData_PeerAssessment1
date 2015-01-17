# Reproducible Research: Peer Assessment 1


## Loading and preprocessing the data

```r
raw.data <- read.csv(file = "activity.csv")
```

##Histogram of the total number of steps taken each day

```r
library(dplyr)
by.day <- group_by(raw.data, date)
day.summary <- by.day %>% summarise(total = sum(steps,na.rm = T))
hist(day.summary$total, xlab = "Number of steps", main = "Total number of steps taken each day")
```

![](PA1_template_files/figure-html/unnamed-chunk-2-1.png) 

## Mean and median total number of steps taken per day

```r
mean(day.summary$total)
```

```
## [1] 9354.23
```

```r
median(day.summary$total)
```

```
## [1] 10395
```

## What is the average daily activity pattern?
###Time series plot:

```r
by.interval <- group_by(raw.data, interval)
interval.summary <- by.interval %>% summarise(mean = mean(steps, na.rm = T))
plot(x = interval.summary$interval, y = interval.summary$mean,type = "l", xlab = "Interval", ylab = "Average steps")
```

![](PA1_template_files/figure-html/unnamed-chunk-4-1.png) 

###Which 5-minute interval, on average across all the days in the dataset, contains the maximum number of steps?

```r
interval.summary$interval[which.max(interval.summary$mean)]
```

```
## [1] 835
```

## Imputing missing values



## Are there differences in activity patterns between weekdays and weekends?
