# ZS-Young-Data-scientist-2018-Winner-rank-3-Solution-
# online phase I - rank 9/4743 participants
# offline phase II - rank 3/43 selected participants (please read notebook for detailed approach)

----------------------------------------------------------------------------------------------------------------------
# Approach for online phase I

----------------------------------------------------------------------------------------------------------------------
                                              Cleaning Approach

----------------------------------------------------------------------------------------------------------------------
In this process, I observed that both train and test data has years and moths separated in two columns
So, in order to make a visualization, we need to make date with these years and months features. So, I created 
the date column in both test and train data.
After this, it appears to be that train data has week wise distribution of records, so we need to convert it into
month wise distribution to make our train data equivalent to test data.	
So, i simply aggregate the sales info on Year - Month - Product_ID - country wise
and sum all the weekly sales to convert it into month wise data which should match test data.

----------------------------------------------------------------------------------------------------------------------
                                                  EDA Approach

----------------------------------------------------------------------------------------------------------------------

In this process, i performed an indepth EDA with decompostion of all the time series into trends, seasons and residual component.
During this EDA, i performed a rigrous parameter search for ARIMA and then verifying with digonsotic report whether everytihng is
ystematic or not. With this parameter search, have obtained some good parameters for each of the product-country pair ARIMA model.

----------------------------------------------------------------------------------------------------------------------
                                              Modeling Approach

----------------------------------------------------------------------------------------------------------------------

After this, I tried to make a baseline with fbprophet package of facebook because it provides a quiet 
comparative forecast without much mannual tunning. with this i scored  1.60559
. After this, i get a decent baseline, now there was need for another good baseline, so i tried another famous method of holts_winter 
forecasting techanique. With this technique, i got another improvement and scored 1.73195 on leaderboard. 
Now it was a good time to start error analysis, so i plotted the forecastig of holts winter and observed that in some cases, there was 
a transparent error, so to manage this, I tried to fit ARIMA model. With the parameter obrtained during searching in EDA, ARIMA gives 
me a score of ~1.70 which wasn't imrovement on previous holts model. Now, I decided to correct errors of HOLTS winter model with ARIMA
, So i plotted the holts and ARIMA forecast crossed over each other to better visualize the performance of each of the model on the test 
data set comparing with train dataset. With this error correction, I imroved my leaderboard score to 1.76017. Then i tried aggregating 
multiple models so that here error can be balanced. This method is simply averaging of multiple models without any weights to increase 
diversity between models and this approach works very good for me and my leadervboard score jumped to 1.79550, Now my submission limit burned out. :)							
