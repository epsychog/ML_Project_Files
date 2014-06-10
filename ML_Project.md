How Well Do Weight Lifting Exercises are Performed?
========================================================

## Synopsis
The current report is a project aiming to predict the manner in which a person performed a weight lifting exercise. The data for this analysis was collected from sensors fitted onto specific parts of the body of 6 participants while performing the exercise.

For this analysis we tried 5 different prediction models and concluded that the **Random Trees** algorithm was the one that gave the best accuracy prediction (**>95%**) and the lower out of sample error (**<5%**)

## Data Processing & Model Selection

### Pre-Processing & Data Cleaning
The data for this project comes from [http://groupware.les.inf.puc-rio.br/har][1].
[1]: http://groupware.les.inf.puc-rio.br/har

We started by examining the variables in the training and test data sets in order to decide which variables to use when training our model. We removed all columns that had a majority of NA values and all columns of class "factor". We also removed the column "X".

At the end of the data processing we ensured that both data sets (training and test) had the same columns selected with the only difference the outcome variable which was column **classe** in the training set and the column **problem_id** in the test set.




### Splitting the Data
We split the training data set into 3 parts
* training (60%)
* cross-validation (20%)
* test (20%)




### Model Fitting & Selection
We selected 5 models to test with our data set based on the following criteria:

1. The type of project that each method was most suitable for (i.e. Classification, Regression or Both). 
2. Our familiarity with the model.

As our project involves a classification project, we selected only models suitable for either Classification or for both classification and regression. Specifically, the models tested were the following:

* Decision Trees (rpart)
* Random Forests (rf)
* Boosting with Trees (gbm)
* Linear Discriminant Analysis (lda)
* Naive Bayes (nb)

Initially we tried to train our models on the training partition we created which corresponded to 60% of the training set. However we found that the algorithms Random Forests, GBM and Naive Bayers were taking a very long time to run so we decided to training our algorithm on 1000 observations selected randomly from the training partition we created.

We trained each of the 5 models on the 100 observations and checked the accuracy of each one using the test partition we created form the training set.




The summarised accuracy results from each model trained are shown below:

1. Decision Trees (rpart): **0.5029314**
2. Random Forests (rf): **0.9576854**
3. Boosting with Trees (gbm): **0.956156**
4. Linear Discriminant Analysis (lda): **0.7035432**
5. Naive Bayes (nb): **0.6721897**

The models that give the best accuracy were the **Random Forests** and **Boosting with Trees (gbm)**. The Random Forest accuracy was a slightly better and this is why we chose this model.

### Cross Validation
The process for cross-validation that we followed consists of the following steps:

1. Split the training data set into 3 parts: training, cross validation and test. 
2. Used 1000 observations from the "training" partition of our training dataset to train our 5 models
3. Used the "test" partition of our training dataset as an independent set to predict the **classe** variable and check the prediction accuracy of each of the 5 models
4. Used the "cross-validation" partition of our training dataset ONLY ONCE with the selected model (Random Forests) and got the out of sample error.




### Estimation of Out of Sample Error
Our estimated out of sample error was **0.04537344** and was derived from the accuracy returned when we run our selected model (Random Forests) on the "cross-validation" partition of our training dataset.

## Conclusion
The **Random Forests** algorithm was the algorithms that performed best among the 5 different prediction models that were tested. The Random Trees algorithm gave the best accuracy prediction (**>95%**) and the lower out of sample error (**<5%**).
