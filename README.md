
## Our goal 

What is the "Best Fitting Line" for my dataset "insurance.csv"?.  I moved along most of the necessary steps in order to execute a complete and careful finding best fit model workflow.I did a whole changes and transformation to the original data as imported from the "csv". I seperated my dataset for training and testing set. Separating data into training and testing sets is an important part of evaluating models. Typically, when you separate a data set into a training set and testing set, most of the data is used for training, and a smaller portion of the data is used for testing. Analysis Services randomly samples the data to help ensure that the testing and training sets are similar. By using similar data for training and testing, you can minimize the effects of data discrepancies and better understand the characteristics of the model. After a model has been processed by using the training set, you test the model by making predictions against the test set. Because the data in the testing set already contains known values for the attribute that you want to predict, it is easy to determine whether the model's guesses are correct.


The metrics chosen to evaluate the model are very important. Residual Standard Error( RSE), R-Squared <img src="https://render.githubusercontent.com/render/math?math=(R^2)">, Adjusted R-Squared <img src="https://render.githubusercontent.com/render/math?math=(Adj R^2)"> , Mean Square Errors (MSE) and Root Mean Squared Errors (RMSE) are very popular metrics for regressors. These metrics are used to measure the performance of making predictions. However, a model fits the data well if the differences between the observed values and the model's predicted values are small and unbiased. Before you look at the statistical measures for goodness-of-fit, you should check the residual plots, for example. Residual plots can reveal unwanted residual patterns that indicate biased results more effectively than numbers. When your residual plots pass muster, you can trust your numerical results and check the goodness-of-fit statistics.  Four principal assumptions justify the use of linear regression models for purposes of inference are :

The metrics chosen to evaluate the model are very important. Residual standard error( RSE), R-Squared <img src="https://render.githubusercontent.com/render/math?math=(R^2)">, Adjusted R-Squared <img src="https://render.githubusercontent.com/render/math?math=(Adj R^2)"> , Mean Square Errors (MSE) and Root Mean Squared Errors (RMSE) are very popular metrics for regressors. These metrics are used to measure the performance of making predictions. However, a model fits the data well if the differences between the observed values and the model's predicted values are small and unbiased. Before you look at the statistical measures for goodness-of-fit, you should check the residual plots, for example. Residual plots can reveal unwanted residual patterns that indicate biased results more effectively than numbers. When your residual plots pass muster, you can trust your numerical results and check the goodness-of-fit statistics.  There are four principal assumptions which justify the use of linear regression models for purposes of inference :



1. linearity and additivity of the relationship between the dependent and independent variables. (test1)

2. statistical independence of the errors (in particular, no correlation between consecutive errors in the case of time series data) (test2)

3. homoscedasticity (constant variance) of the errors (test3)

4. normality of the error distribution. (test4)


If any of these assumptions is violated (i.e., if there are nonlinear relationships between dependent and independent variables or the errors exhibit correlation, heteroscedasticity, or non-normality), then the forecasts, confidence intervals, and scientific insights yielded by a regression model may be (at best) inefficient or (at worst) incredibly biased or misleadi

If any of these assumptions is violated (i.e., if there are nonlinear relationships between dependent and independent variables or the errors exhibit correlation, heteroscedasticity, or non-normality), then the forecasts, confidence intervals, and scientific insights yielded by a regression model may be (at best) inefficient or (at worst) seriously biased or misleading.




## Dataset


This Data is a practical is used in the book Machine Learning with R by Brett Lantz. This book provides an introduction to machine learning using R. All of these datasets are in the public domain but needed some cleaning up and recoding to match the format in the book. The following data obtained from Kaggle explain the cost of a small sample of USA population Medical Insurance Cost based on some attributes :

age: age of the primary beneficiary.
Sex: insurance contractor gender, female, male.
BMI: Body mass index, providing an understanding of the body, weights that are relatively high or low relative to height, objective index of body weight <img src="https://render.githubusercontent.com/render/math?math=(kg / m^2)">. using the ratio of height to weight, ideally 18.5 to 24.9.
children: Number of children covered by health insurance / Number of dependents.
Smoker: Smoking.
Region: the beneficiary's residential area in the US, northeast, southeast, southwest, northwest.
Charges: Individual medical costs billed by health insurance.

## Our Model 

I suggest a model based on an individual's features such as age, physical/family condition, and location against their existing medical expense (charges) to predict future medical expenses of individuals that help medical insurance decide on charging the premium. I notice that the increase between age and the charges is not linear; the older one gets, an even larger amount of medical expenses is used than a year prior, so a square term of the age,  age2 is added instead to age.


Moreover, realizing that the increase in medical expenses is much higher for smokers than for those with each unit increase of BMI from the previous multiple regression model makes it reasonable to assume that the effect of smoking on medical expenses is a lot more. An obese smoker is spending even more on medical than it was for an individual with obesity or is a smoker alone. Because individual is more proned to getting various healthy related issues when s/he is obese and smoking together. So an interaction term of $bmi30*smoker$ is added. One can observe that the newly added terms, age2 and <img src="https://render.githubusercontent.com/render/math?math=bmi30*smokers">, are all significant by p-values, which means that these terms are reasonable to be used in the model. In my model, I used powerTransform and Box-Cox, a family of transformations designed to reduce non-normality of the linear model errors. It turns out that in doing this, it often reduces non-linearity as well. 



