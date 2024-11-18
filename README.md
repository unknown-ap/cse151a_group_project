# Milestone 2
## Preprocessing Steps

We plan to normalize the columns in our dataframe excluding the "Country" column using min max normalization because the data doesn't appear to be normally distributed. We do not need to deal with missing data because we have no missing data. We also will remove outliers. 

# Milestone 3
## What we did for Preprocessing

We dropped all nan values, just in case there were any (it turns out there weren't). Then we scaled the data using a MinMaxScaler to get every feature between 0 and 1. Our model seemed to do very well, with an MSE of ~1.25% on training data, and ~1.48% on the testing data. We performed K-fold cross validation on the model and saw similar error across each set, which was great! 

Where does our model fit in the fitting graph: Our model is the simplest possible model that you could have for the set of features that we are training on, which is a liear model. This means it is on the left side of the fitting graph, end either is underfitting or fitting the data well. We hope to test out higher order polynomial models next milestone and evaluate if our model truly is underfitting or if the linear model is indeed a very representative model. 

What models are we thinking of and why: We are thinking of trying models trained on polynomial transformations of the dataset, as we feel that is the logical next step after training our first really basic linear model. Going forward, we also were thinking of trying to add a feature to the model by encoding the 'County' column instead of dropping it, to see if that feature has any impact on life expectancy based off of this dataset. 


## Conclusion: 

From training this first model, we've learned that there (as we expected) the features do have an influence on life expectency, and that even with a simple linear model we can predict life expectancy fairly well. We want to increase the model complexity later on, and we will need to be careful of increasing it too much to the point of over-fitting, but we'll check for that :)
To improve our model, we will try feature transformations such as polynomial transformations and log transformations.
