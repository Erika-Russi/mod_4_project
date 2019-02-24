# Time Series on U.S. Immigration 1820 - 2017

## Abstract
[Slides](https://docs.google.com/presentation/d/1Dd_srSt6hCC0VHzBVQKHEnJWmmlDE71OH07LxB9ks0o/edit#slide=id.p)

We built a Time Series ARIMA model with SARIMAX to predict immigration as a percentage of U.S. population through 2038, using immigration data from 1820-2017. We validated our model by using one-step ahead forecasting, resulting in a Mean Absolute Percentage Error (MAPE) of 5.01%. We also created a separate model that added GDP as the second variable to predict immigration with Vector Autoregression (VAR).


## Motivation
Inspired by one of the [best visualizations of 2018](https://qz.com/1513260/the-best-data-visualization-in-2018-according-to-data-visualization-experts/), [Simulated Dendrochronology of U.S. Immigration 1790-2016,](https://web.northeastern.edu/naturalizing-immigration-dataviz/#_ga=2.83255134.915890487.1547828814-1702138034.1547828814) we wanted to perform a time series analysis on U.S. Immigration because it is a unique data set, spanning centuries.


## Research
Initially, we were curious to investigate immigration trends by continent and, potentially, by country. However, the level of detail by both continent and country trickled off going back further than [two decades](https://www.dhs.gov/immigration-statistics/yearbook/1996_1999) and if data was available, it was only available by decade.


## Dataset
Since we wanted to perform an analysis looking at a wide time range, we decided to review the [annual total immigration](https://www.dhs.gov/immigration-statistics/population-estimates/unauthorized-resident) starting in the year 1820. Below is a graph of the data, with the two World Wars highlighted grey and the start of the Great Depression marked with a single black line. It is difficult to view any overall trend or seasonality with the initial visualization of the immigration data.  

<p align="center">
  <img width="1000" alt="1" src="https://github.com/Erika-Russi/mod_4_project/blob/master/images/imm_num_by_year.png">
</p>


## Stationarity
Prior to building a model, we needed to stationarize our data. We performed the [Dickey-Fuller Test](https://en.wikipedia.org/wiki/Dickey%E2%80%93Fuller_test) (DF test) on the immigration time series to see how stationary our data was to begin with. Upon running the DF test, we saw that our data was not stationary enough to proceed with modeling since our Critical Value of -2.88 was less than our Test Statistic of -1.04.


  <img width="600" alt="2" src="https://github.com/Erika-Russi/mod_4_project/blob/master/images/imm_num_by_year_RM_SD.png">



  <img width="100" alt="3" src="https://github.com/Erika-Russi/mod_4_project/blob/master/images/imm_num_by_year_DF1.PNG">



## Correlation / Autocorrelation


## Decomposition


## SARIMAX


## ARIMA Model Validation
 forecasts at each point are generated using the full history up to that point.


## Forecasting Immigration 2018 - 2038
- for next 20 years


## Multivariate Analysis

introducedexogenous variable and performed a multivariate analysis
● Performed further multivariate analysis using  to include GDP as variable to predict immigration

