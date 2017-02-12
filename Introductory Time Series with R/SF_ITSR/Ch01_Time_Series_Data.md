---
title: "1. Time Series Data"
output: html_notebook
---
<!-- toc orderedList:0 depthFrom:1 depthTo:6 -->

* [1. Time Series Data](#1-time-series-data)
  * [1.1 Purpose](#11-purpose)
  * [1.2 Time series](#12-time-series)
  * [1.3 R language](#13-r-language)
  * [1.4 Plots, trends, and seasonal variation](#14-plots-trends-and-seasonal-variation)
    * [1.4.1 A flying start: Air passenger bookings](#141-a-flying-start-air-passenger-bookings)
    * [1.4.2 Unemployment: Maine](#142-unemployment-maine)
    * [1.4.3 Multiple time series: Electricity, beer and chocolate data](#143-multiple-time-series-electricity-beer-and-chocolate-data)
    * [1.4.4 Quarterly exchange rate: GBP to NZ dollar](#144-quarterly-exchange-rate-gbp-to-nz-dollar)
    * [1.4.5 Global temperature series](#145-global-temperature-series)
  * [1.5 Decomposition of series](#15-decomposition-of-series)
    * [1.5.1 Notation](#151-notation)
    * [1.5.2 Models](#152-models)
    * [1.5.3 Estimating trends and seasonal effects](#153-estimating-trends-and-seasonal-effects)
    * [1.5.4 Smoothing](#154-smoothing)
    * [1.5.5 Decomposition in R](#155-decomposition-in-r)
  * [1.6 Summary of commands used in examples](#16-summary-of-commands-used-in-examples)
  * [1.7 Exercises](#17-exercises)

<!-- tocstop -->

# 1. Time Series Data
## 1.1 Purpose
## 1.2 Time series
## 1.3 R language
```{r id:"iz0uxgow"}
Fact <- function(n) if (n == 1) 1 else n * Fact(n - 1)
Fact(5)
```
## 1.4 Plots, trends, and seasonal variation
### 1.4.1 A flying start: Air passenger bookings
```{r id:"iz0uxgp2"}
data(AirPassengers)
AP <- AirPassengers
AP
```
```{r id:"iz0uxgp7"}
class(AP)
```

```{r id:"iz0uxgpa"}
start(AP); end(AP); frequency(AP)
```
```{r id:"iz0uxgpd"}
plot(AP, ylab = "Passengers (1000 ' s)")
```

```{r id:"iz0uxgph"}
layout(1:2)
plot(aggregate(AP))
boxplot(AP ~ cycle(AP))
```

### 1.4.2 Unemployment: Maine
```{r id:"iz0uxgpj"}
www <- "Ch01/Maine.dat"
Maine.month <- read.table(www, header = TRUE)
attach(Maine.month)
class(Maine.month)
```
```{r id:"iz0uxgpn"}
Maine.month.ts <- ts(unemploy, start = c(1996, 1), freq = 12)
```
```{r id:"iz0uxgpr"}
Maine.annual.ts <- aggregate(Maine.month.ts)/12
```
```{r id:"iz0uxgpw"}
layout(1:2)
plot(Maine.month.ts, ylab = "unemployed (%)")
plot(Maine.annual.ts, ylab = "unemployed (%)")
```
```{r id:"iz0uxgq0"}
Maine.Feb <- window(Maine.month.ts, start = c(1996,2), freq = TRUE)
Maine.Aug <- window(Maine.month.ts, start = c(1996,8), freq = TRUE)
Feb.ratio <- mean(Maine.Feb) / mean(Maine.month.ts)
Aug.ratio <- mean(Maine.Aug) / mean(Maine.month.ts)
Feb.ratio
```
```{r id:"iz0uxgq3"}
Aug.ratio
```
```{r id:"iz0uxgq6"}
www <- "Ch01/USunemp.dat"
US.month <- read.table(www, header = T)
attach(US.month)
US.month.ts <- ts(USun, start=c(1996,1), end=c(2006,10), freq = 12)
plot(US.month.ts, ylab = "unemployed (%)")
```


### 1.4.3 Multiple time series: Electricity, beer and chocolate data

```{r id:"iz0uxgq9"}
www <- "Ch01/cbe.dat"
CBE <- read.table(www, header = T)
CBE[1:4, ]
class(CBE)
```
```{r id:"iz0uxgqc"}
Elec.ts <- ts(CBE[, 3], start = 1958, freq = 12)
Beer.ts <- ts(CBE[, 2], start = 1958, freq = 12)
Choc.ts <- ts(CBE[, 1], start = 1958, freq = 12)
plot(cbind(Elec.ts, Beer.ts, Choc.ts))
```
```{r id:"iz0uxgqe"}
AP.elec <- ts.intersect(AP, Elec.ts)
```

```{r id:"iz0uxgqh"}
start(AP.elec)
```

```{r id:"iz0uxgqk"}
end(AP.elec)
```

```{r id:"iz0uxgqn"}
AP.elec[1:3, ]
```
```{R id:"iz0uxgqq"}
AP <- AP.elec[,1]; Elec <- AP.elec[,2]
layout(1:1)
plot(AP, main = "", ylab = "Air passengers / 1000's")
plot(Elec, main = "", ylab = "Electricity production / MkWh")
plot(as.vector(AP), as.vector(Elec),
xlab = "Air passengers / 1000's",
ylab = "Electricity production / MWh")
abline(reg = lm(Elec ~ AP))
```
```{r id:"iz0uxgqt"}
cor(AP, Elec)
```

### 1.4.4 Quarterly exchange rate: GBP to NZ dollar

```{r id:"iz0uxgqw"}
www <- "Ch01/pounds_nz.dat"
Z <- read.table(www, header = T)
Z[1:4, ]
```

```{r id:"iz0uxgqz"}
Z.ts <- ts(Z, st = 1991, fr = 4)
plot(Z.ts, xlab = "time / years",
     ylab = "Quarterly exchange rate in $NZ / pound")
```


```{r id:"iz0uxgr3"}
Z.92.96 <- window(Z.ts, start = c(1992, 1), end = c(1996, 1))
Z.96.98 <- window(Z.ts, start = c(1996, 1), end = c(1998, 1))
layout (1:2)
plot(Z.92.96, ylab = "Exchange rate in $NZ/pound",
     xlab = "Time (years)" )
plot(Z.96.98, ylab = "Exchange rate in $NZ/pound",
     xlab = "Time (years)" )
```

### 1.4.5 Global temperature series
```{r id:"iz0uxgr8"}
www <- "Ch01/global.dat"
Global <- scan(www)
Global.ts <- ts(Global, st = c(1856, 1), end = c(2005, 12),
                fr = 12)
Global.annual <- aggregate(Global.ts, FUN = mean)
plot(Global.ts)
plot(Global.annual)
```
```{r id:"iz0uxgrb"}
New.series <- window(Global.ts, start=c(1970, 1), end=c(2005, 12))
New.time <- time(New.series)
plot(New.series); abline(reg=lm(New.series ~ New.time))
```

* 8 For general policy documents and discussions on climate change, see the website (and links) for the United Nations Framework Convention on Climate Change at http://unfccc.int.  

* 9 The data are updated regularly and can be downloaded free of charge from the Internet at: http://www.cru.uea.ac.uk/cru/data/.  

* 10 For example, refer to US Energy Information Administration at http://www.eia.doe.gov/emeu/aer/inter.html.  


## 1.5 Decomposition of series

### 1.5.1 Notation

### 1.5.2 Models

```
11 Refer to http://unfccc.int.  

12 Some books do distinguish explicitly by using lowercase for the time series and uppercase for the model.  
```

### 1.5.3 Estimating trends and seasonal effects

### 1.5.4 Smoothing

### 1.5.5 Decomposition in R
```{r id:"iz0uxgre"}
plot(decompose(Elec.ts))
Elec.decom <- decompose(Elec.ts, type = "mult")
plot(Elec.decom)
Trend <- Elec.decom$trend
Seasonal <- Elec.decom$seasonal
ts.plot(cbind(Trend, Trend * Seasonal), lty = 1:2)
```

## 1.6 Summary of commands used in examples
| **read.table**   | reads data into a data frame                                       |
|--------------|--------------------------------------------------------------------|
| **attach**       | makes names of column variables available                          |
| **ts**           | produces a time series object                                      |
| **aggregate**    | creates an aggregated series                                       |
| **ts.plot**      | produces a time plot for one or more series                        |
| **window**       | extracts a subset of a time series                                 |
| **time**         | extracts the time from a time series object                        |
| **ts**.intersect | creates the intersection of one or more time series                |
| **cycle**        | returns the season for each value in a series                      |
| **decompose**    | decomposes a series into the components trend, seasonal effect, and residual|
| **stl**          | decomposes a series using loess smoothing                          |
| **summary**      | summarises an R object                                             |

## 1.7 Exercises
