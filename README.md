# Covid-19-Modeling
An exploration into COVID 19 Temporal Statistics with extensive modeling, visualization, and prediction.
## Problem

The severity of COVID became and remains a contested topic. There also remains criticism in how different political leaders have approached the issue. While trying to see what characteristics of a county may be indicative of how hard COVID impacted different areas, we questioned whether the population of a county would be correlated with the number of COVID cases identified. As a result, we propose the null hypothesis that the number of COVID cases per capita is not correlated with the population of a county. Likewise, our alternative hypothesis is that the number of COVID cases per capita is positively correlated with the population of a county. Counties were classified as small, medium, or large depending on if their 2020 population fell in the lower, middle, or upper third of county population sizes in 2020.
![alt text](https://github.com/JerryLiu-dev/Covid-19-Modeling/blob/main/images/c1.PNG)
                    
>**New COVID Cases in the past week per capita for different sized counties vs Time**

## Modeling

We first decided to use an A/B test to compare distributions because we suspected that there may be an association between cases per capita and county size. From the boxplot in Figure 2, we can observe that medium counties had more cases per capita on average. However, the differences in cases per capita between groups was not extremely different, so we wanted to see if the observed differences were due to chance or actually significant.

Our group also decided to create and train a random forest model to predict the size of different counties based on the number of COVID cases and GDP per capita of each county. The inputs of the model are cases per capita and GDP per capita, both numeric variables. The output of the model is county size, a categorical variable. We chose to focus the project on identifying an association, rather than forecasting cases in the upcoming days. As a result, we used cases per capita as a predictor. This is preferable to using county size as a predictor because county size has only 3 potential values: small, medium, and large. Having so few unique values when there already does not seem to be much variation between the groups would make our predictor inaccurate and provide little insight. 

GDP per capita was included as a feature because a county with a higher GDP per capita would have a larger pool of money at their disposal for their county’s COVID response, possibly leading to a decrease in COVID cases within their county. GDP may also be associated with instrumental variables such as education and population density. As expected, including it increased the accuracy of the model.

During the process of choosing which type of model to use for our data, our group experimented with decision tree models, logistic regression models, and random forest models. After running our data inputs through each, we found that the random forest model gave us highest improvement accuracy-wise, increasing from an accuracy of 41% to 48% while the decision tree model peaked at 45% accuracy and the logistic regression peaked at 48% accuracy as seen in Figure 1. In addition to that, several advantages of the random forest model complemented our data selection quite well. It worked well with the categorical and quantitative variables we had, and did not require us to normalize the input values. These factors led our group to decide on utilizing the random forest model.

![alt text](https://github.com/JerryLiu-dev/Covid-19-Modeling/blob/main/images/c2.PNG)

## Random Forest Classifier

With an accuracy of 48% for the testing set for our random forest model, we fail to reject the null hypothesis. The null hypothesis states that the number of COVID cases per capita and population size & GDP are not correlated, as it is below 62.50% accuracy. The random forest model’s predicted and actual values can be seen in Figure 3 below, with GDP per capita as the x-axis, cases per capita as the y-axis, classified values as the points, and predicted values as the background. Visually, if county size is a significant factor, there would be horizontal blocks of color in the area where the data points are clustered (approximately 0<y<0.2, 25<x<80). This is not the case here, as green, orange, and blue are randomly dispersed throughout the area of interest.


![alt text](https://github.com/JerryLiu-dev/Covid-19-Modeling/blob/main/images/c3.PNG)
