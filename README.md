# ZS-Young-Data-scientist-2018-Winner-rank-3-Solution-
# online phase I - rank 9/4743 participants
# offline phase II - rank 3/43 selected participants (please read notebook for detailed approach)

----------------------------------------------------------------------------------------------------------------------
# Approach for online phase I

----------------------------------------------------------------------------------------------------------------------
                                              Cleaning Approach

----------------------------------------------------------------------------------------------------------------------
In this process, I observed that both train and test data has years and months separated in two columns
So, in order to make a visualization, we need to extract date with these years and months features. So, I created 
the date column in both test and train data. After this, it appears that train data has week wise distribution of records, so we need to convert it into month wise distribution to make our train data equivalent to test data. So, I simply aggregate the sales info on Year - Month - Product_ID - country wise and sum all the weekly sales to convert it into month wise data which now will match test data.

----------------------------------------------------------------------------------------------------------------------
                                                  EDA Approach

----------------------------------------------------------------------------------------------------------------------

In this process, I performed an indepth EDA with decompostion of all the time series into trends, seasons and residual component.During the EDA, I performed a rigrous parameter search for ARIMA and then verifying with digonsotic report whether everytihng is systematic/relevant or not. With this parameter search, have obtained some good parameters set for each of the product-country pair ARIMA model.

----------------------------------------------------------------------------------------------------------------------
                                              Modeling Approach

----------------------------------------------------------------------------------------------------------------------

After this, I tried to make a baseline with fbprophet package of facebook because it provides quiet a comparative forecast without much mannual tunning. with this I scored  1.60559. After this, I get a decent baseline, now there was a need for another good improvement, so i tried another famous method of holts_winter forecasting techanique. With this technique, I got another improvement and scored 1.73195 on leaderboard. Now it was a good time to start error analysis, so I plotted the forecastig of holts winter and observed that in some cases, there was a transparent error, so to manage this, I tried to fit ARIMA model. With the parameter obtained during searching in EDA, ARIMA gives me a score of ~1.70 which wasn't imrovement on previous holts model. Now, I decided to correct errors of HOLTS winter model with ARIMA, So I plotted the holts and ARIMA forecast crossed over each other to better visualize the performance of each of the model on the test data set comparing with train dataset. With this error correction, I imroved my leaderboard score to 1.76017. Then I tried aggregating multiple models so that here error can be corrected. This method is simply averaging of multiple models without any weights to increase diversity between models and it worked good for me and my leadervboard score jumped to 1.79550, Now my submission limit burned out. :)							
