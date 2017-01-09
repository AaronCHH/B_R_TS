---
title: "Ch01 Time Series Data"
output: html_notebook
---
## 1.1_Purpose 15
## 1.2_Time series 16
## 1.3_R language 17
```{r}
Fact <- function(n) if (n == 1) 1 else n * Fact(n - 1)
Fact(5)
```
## 1.4_Plots, trends, and seasonal variation 18
### 1.4.1_A flying start: Air passenger bookings 18
```{r}
data(AirPassengers)
AP <- AirPassengers
AP
```
```{r}
```
### 1.4.2_Unemployment: Maine 21
### 1.4.3_Multiple time series: Electricity, beer and chocolate data 24
### 1.4.4_Quarterly exchange rate: GBP to NZ dollar 28
### 1.4.5_Global temperature series 30
## 1.5_Decomposition of series 33
### 1.5.1 Notation 33
### 1.5.2 Models 33
### 1.5.3 Estimating trends and seasonal effects 34
### 1.5.4 Smoothing 35
### 1.5.5 Decomposition in R 36
## 1.6_Summary of commands used in examples 38
## 1.7_Exercises 38
