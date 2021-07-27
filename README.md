# CHANDAN KUMAR (BATCH 3)- GOOGLE COLAB / TIME SERIES 4-5 : 
## (Rahul Agnihotri(T.L))


# Exponential Smoothing: Single, Double and Triple Exponential Smoothing

# Introduction
--------------------------
1. Exponential smoothing is a rule of thumb technique for smoothing time series data using the exponential window function.
2. This is a popular method to produce smoothed time series. Similar to Weighted and Exponential Moving Average methods.
3. Exponential Smoothing also assigns exponentially decreasing weights as the observation get older.
4. It differs from moving average in the way it assumes it initial values and use of past value in calculation.
5. Another difference between the moving average methods and Exponential smoothing is in how the weights are attained.
6. In exponential smoothing, there are one or more smoothing parameters to be determined (or estimated) and these choices determine the weights assigned to the observations. This article provides an overview of exponential smoothing methods with worked out examples. There three models of forecast in exponential smoothing such as Single, Double and Triple Exponential Smoothing.

# SUMMARY
-------------------------------------------------------------------------------------------------------------------------------------

# Single Exponential Smoothing (SES)
------------------------------------
•      To define the basic equation of SES, lets’ consider Yt as the time series data, α as the smoothing parameter and St is the ‘smoothed’ time series data. In the basic equation of SES, the next smoothed data point starts with previous smoothed data point and the previous observed data point. It would be easy to understand with an equation as follows,

![image](https://user-images.githubusercontent.com/70132200/127117695-11a09507-bfd7-44ff-a456-17b85738a5e1.png)

•      Where α is the given weight which is subject to 0 < a < 1. What is α? Alpha (α) is the smoothing constant whose value ranges from zero to one.

•      The speed at which the older responses are dampened (smoothed) is a function of the value of α. When α is close to 1, dampening is quick and when α is close to 0, dampening is slow.

•      Here dampening means reducing the influence of past values. Damping factor is responsible to assigns the least value to distant data points. Technically, the damping factor is 1 minus the alpha level (1 – α).

•      Damping factors are used to smooth out the graph and take on a value between 0 and 1. Thus smoothing constant and damping factors are inversely proportional. Larger dampening factors smoothes out the peaks and valleys more than smaller damping factors. Smaller damping factors also mean that the smoothed values are closer to the actual data points than larger damping factors. The alpha value with least mean square error (MSE) is the best for the model.


# For the 2nd smoothed data point (S2), the equation would be just Y1, because S1 does not exists. Every smoothed data point depends upon previous observed as well as smoothed data point, hence S1 does not exists. The smoothed series starts with the smoothed version of the second observation. For the 3rd smoothed data point (S3), the equation would be,
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

![image](https://user-images.githubusercontent.com/70132200/127118300-aa7a1541-fe56-43ca-accd-0eee1877d01c.png)

•      It should be noted that, as with averaging methods, SES can only produce a one-step forecast just as MA.

![image](https://user-images.githubusercontent.com/70132200/127118464-8d4ef4b8-70d8-4804-88e1-e1be0a89cabc.png)



# Double Exponential Smoothing (DES)
------------------------------------

# Holt’s Linear Trend method is the other name of Double Exponential Smoothing (DES). This is an extension of exponential smoothing to take into account a possible (local) linear trend. This extension of SES was done by Charles E. Holt in the year 1957. Here are the two equations associated with Double Exponential Smoothing.

![image](https://user-images.githubusercontent.com/70132200/127118673-1b3ba28e-4d35-4ce3-86c8-cf3c5b7d058e.png)

•      The current value (Yt) of the series itself is used to calculate its smoothed value is the replacement in double exponential smoothing.


•      A value of α is chosen to smooth the series and adapt to changes in level. A value of γ is chosen to allow the trend estimate to react to changes in the rate of growth of the series. There are two smoothing equations and a forecast equation. 

•      The equation (1) is the level equation and the equation (2) is the trend equation. In the equation (1), the smoothed value is estimated directly by adding the past smoothed value (St-1) to the previous value of trend (bt-1).

•      This helps to eliminate the lag and bring St to the appropriate base of the current data point. Thus the level equation St is a weighted average of observation Yt and the one-step-ahead training forecast for time t, given by St−1+bt−1. In the equation (2), bt is a weighted average of the estimated trend at time t based on St−St−1 and bt−1, the previous estimate of the trend. If the γ values are very small the trend (slope) hardly changes over time.

•      One might consider that stationary data are simply a special case of the more general trended process where the trend component is equal to zero.

•      Following this logic, we could use a trend model without regard to whether the demand was stationary or trended. However, procedures such as Double Smoothing or Holt's technique should only be used if the data really are trended; otherwise, the MSE will be inflated because these procedures "look" for trend. To estimate the forecast at time t, the values of St and Bt are estimated and then the equations (1) and (2) are combined as follows,

![image](https://user-images.githubusercontent.com/70132200/127119110-58750e8f-7bc3-45d8-a2e1-6934c3b4d47d.png)


•      Here St and bt are respectively (exponentially smoothed) estimates of the level and linear trend of the series at time t, whilst Yt+1 is the linear forecast. It should be noted that to use this method it is not necessary for a series to be completely linear, but some trend should be present.



# Triple Exponential Smoothing (TES)
------------------------------------

# Holt-Winters' Trend Method is also called as triple exponential smoothing (TES). Holt (1957) and Winters (1960) extended Holt's model to capture Seasonality (It) along with trend. There are two models based on the structure of trend; Holt-Winter's Linear trend model and Holt-Winter's Exponential trend model.
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------


•      n turn these models can also be classified based on the nature of seasonal component as multiplicative and additive models. The multiplicative method should be used when seasonal variability is amplified with time, whereas the additive approach is more suitable in the case of constant seasonal variability.

•      Whenever in doubt, both methods can be implemented and the best one chosen based on the error it generates.

![image](https://user-images.githubusercontent.com/70132200/127119507-8f852812-08b0-4d12-8668-bd5d8d2a1c88.png)

•      Brown’s linear trend and Damped trend models are not covered within this article. The equations for the different Holt-Winter model are presented in the table below. Consider, Yt as the time series data with trend and seasonality components. TES or Holt-Winter's has one forecast equation (Ft) and three smoothing equations:

•      St for level component or overall smoothing equation; bt for trend component; and It for seasonality component. There are three smoothing constants α, β and γ. L here denotes the frequency of the seasonality, i.e., the number of seasons in a year. For example, for quarterly data L=4, and for monthly data L=12. 

![image](https://user-images.githubusercontent.com/70132200/127119630-237c6895-ae71-4f47-81f8-47539006507f.png)

# Where 0 < α ≤ 1, 0 ≤ γ ≤ 1 and 0 ≤ β ≤ 1–α. The small value of β for the multiplicative model means that the seasonal component hardly changes over time.	The smoothing parameters are chosen based on the comparatively lesser measures of error.  The method of choosing the Initial values differs among researchers, some use zero as initia value while some use last year value as initial value.

 
 
