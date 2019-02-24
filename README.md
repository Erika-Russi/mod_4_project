# Time Series on U.S. Immigration 1820-2017

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

### Total Immigration
Prior to building a model, we needed to stationarize our data. We performed the [Dickey-Fuller Test](https://en.wikipedia.org/wiki/Dickey%E2%80%93Fuller_test) (DF test) on the immigration time series to see how stationary our data was to begin with. Upon running the DF test, we saw that our data was not stationary enough to proceed with ARIMA modeling since our Critical Value of -2.88 was less than our Test Statistic of -1.04 and our p-value was not less than our .05 target.

<p align="center">
  <img width="800" alt="2" src="https://github.com/Erika-Russi/mod_4_project/blob/master/images/imm_num_by_year_RM_SD.png">
</p>
<p align="center">
  <img width="400" alt="3" src="https://github.com/Erika-Russi/mod_4_project/blob/master/images/imm_num_by_year_DF1.PNG">
</p>

We proceeded with various transformations of the series to achieve stationarity, including log and square root transformations of the data, subtracting the rolling mean and the exponentially weighted moving average, as well as differencing for various periods (10 - 20 years). We achieved the best stationarity by subtracting the exponential rolling mean from our series and differencing by 15 periods. As shown by the DF test, our p-value was well below our .05 target, and our test statistic was now less than our critical value.

<p align="center">
  <img width="800" alt="4" src="https://github.com/Erika-Russi/mod_4_project/blob/master/images/imm_num_by_year_RM_SD-bestone.png">
</p>
<p align="center">
  <img width="400" alt="5" src="https://github.com/Erika-Russi/mod_4_project/blob/master/images/imm_num_by_year_DF2.PNG">
</p>

### Immigration as Percentage of U.S. Population
We also checked the stationarity of our time series when the total immigration numbers were transformed as a percentage of the U.S. population. Based on the results of the DF test, this data was significantly more stationary than our original time series, and with fewer transformations.

<p align="center">
  <img width="800" alt="6" src="https://github.com/Erika-Russi/mod_4_project/blob/master/images/imm_perc_by_year.png">
</p>
<p align="center">
  <img width="400" alt="7" src="https://github.com/Erika-Russi/mod_4_project/blob/master/images/imm_perc_by_year_DF.png">
</p>


## Autocorrelation / Partial Autocorrelation
Once we got the time series to our targeted stationarity, we plotted the autocorrelation and partial autocorrelation (PACF) graphs to assist us with locating the best parameters for our ARIMA model. You can see in the PACF graph that there appears to be some seasonality happening approximately every 15 years.

<p align="center">
  <img width="800" alt="8" src="https://github.com/Erika-Russi/mod_4_project/blob/master/images/autocorrelation.png">
</p>

In an ARIMA model, there are three distinct integer values, (p, d, q).

p= allows us to incorporate the effect of past values into our model. This would be similar to stating that immigration in this year will be similar to the past couple of years.

d = the number of differences; identifies the number of lag values to subtract from the current observation. This would be similar to stating that immigration in this year will be similar to the past couple of years if the difference in the amount of immigration in the last n years is small.

q = Number of MA (Moving Average) terms; sets the error of the model as a linear combination of the error values observed at previous time points in the past


## SARIMAX
To find the best p, d, and q terms for our ARIMA model, we ran a STATSMODELS' SARIMAX to optimize for the lowest [Akaike Information Criterion](https://en.wikipedia.org/wiki/Akaike_information_criterion) values.



These three distinct integer values, (p, d, q), are used to parametrize ARIMA models. Because of that, ARIMA models are denoted with the notation ARIMA(p, d, q)
The next step was 

The next step is to determine the tuning parameters of the model by looking at the autocorrelation and partial autocorrelation graphs. There are many rules and best practices about how to select the appropriate AR, MA, SAR, and MAR terms for the model. The big issue as with all models is that you don’t want to overfit your model to the data by using too many terms.

## ARIMA Model Validation
 forecasts at each point are generated using the full history up to that point.


## Forecasting Immigration 2018 - 2038
- for next 20 years


## Multivariate Analysis

introducedexogenous variable and performed a multivariate analysis
● Performed further multivariate analysis using  to include GDP as variable to predict immigration

