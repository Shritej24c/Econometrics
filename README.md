# Panel Data Study: Determinants of Life Expectancy in Sub-Saharan Africa (SSA)

**What is Life Expectancy?** 

Life expectancy at birth indicates the number of years a newborn infant would live if prevailing
patterns of mortality at the time of its birth were to stay the same throughout its life

The below image clearly shows the disparity in Life Expectancy across different countries in 2019

![image](https://github.com/Shritej24c/Econometrics/blob/main/images/LE%202019.png)


There's a drastic difference in Life Expectancy which points to the scope of improvement in these countries with similar low life expectancy. 

Below are the multiple Bar Charts which show the average Life Expectancy across different regions throughout the world. 

![image](https://github.com/Shritej24c/Econometrics/blob/main/images/le_reg.png) 

The Sub-Saharan African region experiences the lowest life expectancy at birth compared to other regions over the past 3 decades. In the year 2019, the Middle East and North Africa had an average life expectancy of 74.27 years compared to the SSA region’s average life expectancy of 61.6 years. From 2, we can see the variation in average life expectancy across various regions around the world for the last
3 decades. Moreover, SSA countries have consistently ranked as the lowest-earning countries in terms of GDP per capita. Therefore, there is a huge scope for improvement in life expectancy in SSA countries and hence our research focuses on the 40 Sub-Saharan African (SSA) countries with the lowest GDP per capita.

**Research Questions**

In this paper, we aim to have a better understanding of factors affecting life expectancy in the SSA region for an efficient policy-making process, and better allocation of funds and resources in addressing the prevalence of low life expectancy in Sub-Saharan Africa. To achieve that we attempt to answer the following questions in this research:

1. What’s the Impact of Expenditure on Health and Education (% of GDP) on Life Expectancy?
2. How does the prevalence of undernourishment and communicable disease Affect Life Expectancy?
3. Do factors like corruption and unemployment rate impact life expectancy? If yes, quantify
4. Increase in CO2 emissions decrease life expectancy? Is it significant?


**Determinants of Life Expectancy**

1. Health Expenditure (% of GDP)
2. Education Expenditure (% of GDP)
3. Unemployment (% total labor force)
4. Corruption (CPIA rating)
5. Disability-Adjusted Life Years (DALYs) due to Communicable diseases
6. Prevalence of Undernourishment (% of the population)
7. Carbon dioxide emissions (kiloton)

**Data**

Sub-Saharan African (SSA) countries - Low Life Expectancy and low GDP per capita

Main Sources of Data: The World Data Bank and  Our World in Data

Out of 40+ SSA countries, due to a lot of missing values for the indicators chosen, we focused on only 19
countries in that region

No record of CPIA data (corruption rating) for any country before 2005 

Avoided data after 2019 due to the prevalence of COVID

Indicators like Sanitation, Water Supply, and Living standards weren’t available for many countries

Final panel data - N (countries) = 19 & T (years) = 15 (2005-2019) 

**Correlation Matrix**

Correlation matrix among independent variables: 

![image](https://github.com/Shritej24c/Econometrics/blob/main/images/corr_mat.png) 


**PooledOLS**

Pooled OLS can be written as follows: 

![image](https://github.com/Shritej24c/Econometrics/blob/main/images/panel%20equation.png)

**Results - PooledOLS**

![image](https://github.com/Shritej24c/Econometrics/blob/main/images/pooled%20results.png)

From the above results, we observe that our main 2 determinants; health and education came out to be statistically insignificant
and the estimated effect of other variables is not as expected. Let's visit the assumptions for PooledOLS and verify whether they satisfy or not. 


**Assumptions - PooledOLS**

TS.1:  Linear in Parameters - Linearity is ensured by taking functional forms of some variables 

TS.2:  No perfect collinearity - Pearson’s Correlation Matrix reveals no perfect collinearity between the chosen indicators 

TS.3: Contemporaneous Exogeneity - Ensures that estimators are consistent 

TS.4: Homoscedasticity - Can be evaluated by various tests like the White test, Breusch-Pagan test, or just by plotting Residuals vs. Fitted Values and observing their variance 

TS.5 - No Serial Correlation among error term (residuals) - Durbin-Watson test, Ljung-Box test 


**Heteroskedasticity Tests**


![image](https://github.com/Shritej24c/Econometrics/blob/main/images/hetero%20tests.png)

**Residual Plots**

![image](https://github.com/Shritej24c/Econometrics/blob/main/images/heteroscedasticity.png)

**TS. 5: Tests for Serial Correlation**

1. Durbin-Watson-Test: will have one output between 0 – 4. 
    mean (= 2) -  no autocorrelation 
    0 – 2 = positive autocorrelation (the nearer to zero the higher the correlation)
    2 – 4 = negative autocorrelation (the nearer to four the higher the correlation)
        Results: Statistic = 1.64 ( a slight positive autocorrelation)
2. Ljung-Box Test: Checks for autocorrelation between all lags of error residuals
    Results: p-value for all lags < 0.05 (No autocorrelation between residuals)


**TS3. : Contemporaneous Exogeneity**

![image](https://github.com/Shritej24c/Econometrics/blob/main/images/TS3%20Exogeneity.png)

**Individual Fixed Effects Model**

Individual effects of independent variables are fixed over time


![image](https://github.com/Shritej24c/Econometrics/blob/main/images/Fixed%20Effects%20equation.png)

**Fixed Effects Results**

![image](https://github.com/Shritej24c/Econometrics/blob/main/images/fixed%20results.png)

As shown in the above table, we can see that except for undernourishment all the variables are statistically significant. Moreover, variables undernourishment, health, Educ have positive effects on life expectancy, and variables unemployment, corruption, and log_communicable have negative effects, which is as expected. Only log_CO2 has a positive effect which doesn’t make sense. Most importantly, the R-squared of the F.E. is 0.904 which is remarkable and the determinants we considered do a good job of explaining the variation in Life Expectancy.


**Random Effects**

Individual effects of independent variables vary over time

![image](https://github.com/Shritej24c/Econometrics/blob/main/images/random%20effects%20equation.png)

**Results - Random Effects**

Observing the results of the Random Effects, we can see that they almost mirror the F.E results, varying slightly in the estimates. Here, the R-squared is pretty decent as well. After eliminating Pooled OLS as our choice of model, we evaluated for endogeneity to determine the best model between F.E and R.E.

![image](https://github.com/Shritej24c/Econometrics/blob/main/images/random%20results.png)

**Hausman Test - For Endogeneity**

Using the Hausman test to test for covariance between alpha and independent variables. We rejected the
null hypothesis, hence we chose Fixed effects as our final econometrics model to determine the significant
factors and their effect on Life expectancy. The results of the Hausman test can be seen as follows:

![image](https://github.com/Shritej24c/Econometrics/blob/main/images/hausmann.png)

b0 - always consistent; b1 - only consistent under H0

The null hypothesis is rejected, therefore Fixed Effects are preferred over Random Effects since the estimator is consistent.


**Final Model - Fixed Effects Model**


![image](https://github.com/Shritej24c/Econometrics/blob/main/images/final%20equation.png)

From Fixed Effects results - Except for the Prevalence of Undernourishment all variables are significant 
(The below results are concluded by keeping other factors constant)
1. A 1% Increase in CO2 emissions increases Life Expectancy by 0.07 years (not expected)
2. A 1% points increase in health and education expenditure (% of GDP) causes life expectancy to increase by 0.24 and 0.23 years respectively (expected)
3. A 1% point increase in unemployment (% of the total labor force) decreases life expectancy by .17 years (e)
4. 1 point increase in the CPIA rating decreases the life expectancy by 1.1 years (e)
5. A 1% increase in disability-adjusted life year per 100,000 individuals, decreases L.E. by 0.37 years (e)


**Conclusions**

1. Most of our independent variables showed expected significant behavior.
2. An increase in health and education expenditure and a decrease in the unemployment rate and corruption should have a positive ceteris paribus effect on life expectancy.
3. An increase in disability-adjusted life years specifically due to communicable diseases puts the population in danger and lowers the life expectancy of that respective country. The opposite effect was observed of disability-adjusted life years specifically due to non-communicable diseases & injuries.
3. CO2 output has a positive effect on life expectancy due to industrialization.
4. Our analysis shows what the government can do to uplift the life expectancy in these low-income countries and how can it direct the efforts to achieve this goal.


