# Milestone 2
## Preprocessing Steps

We plan to normalize the columns in our dataframe excluding the "Country" column using min max normalization because the data doesn't appear to be normally distributed. We do not need to deal with missing data because we have no missing data. We also will remove outliers. 

# Milestone 3
## What we did for Preprocessing

We dropped all nan values, just in case there were any (it turns out there weren't). Then we scaled the data using a MinMaxScaler to get every feature between 0 and 1. Our model seemed to do very well, with an MSE of .0125 on training data, and .0148 on the testing data. We performed K-fold cross validation on the model and saw similar error across each set, which was great! 

Where does our model fit in the fitting graph: Our model is the simplest possible model that you could have for the set of features that we are training on, which is a linear model. This means it is on the left side of the fitting graph, end either is underfitting or fitting the data well. We hope to test out higher order polynomial models next milestone and evaluate if our model truly is underfitting or if the linear model is indeed a very representative model. 

What models are we thinking of and why: We are thinking of trying models trained on polynomial transformations of the dataset, as we feel that is the logical next step after training our first really basic linear model. Going forward, we also were thinking of trying to add a feature to the model by encoding the 'County' column instead of dropping it, to see if that feature has any impact on life expectancy based off of this dataset. 

# Milestone 4
## What we did for our second model

For our second model, we chose to do polynomial regression because a lot of our data seems to be non-linearly correlated. After training our data using the Pipeline and PolynomialFeatures libraries from sklearn, we saw that when we set the degree to 2, aka added another feature column for each feature where each feature was squared, we found that the MSE improved slightly from 0.0125 to 0.0102 for the training data and went from 0.0148 to 0.0136 on the test data. Seeing this improvement, we wanted to increase the degree to 3, but this resulted in overfitting because our error on the test data increased to 2379.33. 

Where does our model fit in the fitting graph: Our model has become slightly more complex because we are squaring the features now to make it a polynomial model. This means that it is further away from the left side of the fitting graph and may be overfitting the data. When we set the degree to 3, we are definitely overfitting the data, and also increasing complexity, moving our model further to the right side of the fitting graph. 

What models are we thinking of why: For another model, we're thinking of doing specific transformations on each feature based on the distribution of the features or based on the feature's relationship to our y. If the relationship the feature has with our independent variable is more exponential, we may take the log of it to make it more linear. Or if it seems more logarithmic, we may take the square of it to make it more linear as well. Then we will perform linear regression on the transformed data, hopefully making our model more accurate and reducing the MSE and R2. 

# Conclusions for Model 1 and Model 2:
From training this first model, we've learned that there (as we expected) the features do have an influence on life expectency, and that even with a simple linear model we can predict life expectancy fairly well. We want to increase the model complexity later on, and we will need to be careful of increasing it too much to the point of over-fitting, but we'll check for that :)
To improve our model, we will try feature transformations such as polynomial transformations and log transformations.

For training the second model, we want to transform individual features based on the relationship each feature has with life expectancy. In our second model, we ended up squaring every single feature within a polynomial regression, but this may have caused some overfitting, so we hope to improve our model by slightly increasing the model complexity so that each feature can have a more linear relationship with the life expectancy feature we are trying to predict. This is how we plan to improve upon our second model. 

