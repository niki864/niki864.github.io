---
priority: 0.7
title: Volatility Analysis of Bitcoin
excerpt: Technical analysis of Bitcoin prices done in R 
categories: works
background-image: bitcoin.jpg
tags:
  - RStudio
  - TTR
  - ggplot2
---

A technical analysis of bitcoin price history over a period of one year done in the R language utilising the TTR package. This project was done in conjunction with the course IE 6200 : Probability and Statistics for Engineers @ Northeastern University. 

## Packages Required

TTR, downloadable from CRAN

### Prerequisites

R and R Studio

## Base Dataset Description

Dataset is an hourly time series data set with 8 Variables (Timestamp, Open, High, Low, Close, Volume (BTC), Volume (Currency), Weighted Price)
Data gathered is averaged across six hour time interval between sampling, i.e. 0000-0600 hrs, 0600-1200 hrs, 1200-1800 hrs to 1800-2400 hrs.

Base descriptive stats are provided.

Source: *bitcoincharts.com*(https://bitcoincharts.com)

## Data Analysis Description

We first generate Bollinger Bands with a SMA of 28 samples ( 28/4 - Weekly Moving Average equivalent) and obtain pctB values. 
pctB is the percentage of Bitcoin price to the range between the up and lower band. 
<img src="https://user-images.githubusercontent.com/10093954/37727316-e5c0a436-2d0d-11e8-8239-81f3aae6d6f7.jpeg" alt="Drawing" style="width:100%;"/>

There is a measure called pctB. This basically charts the degree of volatility between the current price and the moving average. Using pctB we can scale it to an index measure by taking the absolute value and converting it into percentage points on scale 100.
<img src="https://user-images.githubusercontent.com/10093954/37727315-e5b2d374-2d0d-11e8-8096-2d396a19a25d.jpeg" alt="Drawing" style="width:100%;"/>

The final graph is generated on the basis of a volatility index, I'll call it Vindex. This shows the days in the year where volatility has been excessive. We can infer that on these days, the price has exhibited massive change.
<img src="https://user-images.githubusercontent.com/10093954/37727313-e5007a3a-2d0d-11e8-80a1-85a5cab27129.jpeg" alt="Drawing" style="width:100%;"/>


## Summary

Spikes in graph correlate to significant days in which volatility has exceeded moving average by a large margin. 

## Codebase and License

Here's the full github repo for [this project](https://github.com/niki864/VolatilityAnalysisBitcoin). This project is licensed under the MIT License - see the *LICENSE.md* file in the repo for more details.

## Acknowledgments

* IE 6200 :Probability and Statistics Course @Northeastern University : Prof. Dehghani 

## Feedback

Contact me for any feedback regarding this project. Always eager to hear from fellow data enthusiasts.
