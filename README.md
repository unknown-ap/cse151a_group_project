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

Where does our model fit in the fitting graph: Our model has become slightly more complex because we are squaring the features now to make it a polynomial model. This means that it is further away from the left side of the fitting graph because the x-axis measures complexity. When we increase the polynomial degree, we are increasing the complexity of the model. For our model specifically, we begin overfitting the data when we set the degree to three, so our error drastically increases. When we use lower degrees, our model complexity is lower (but still higher than our first model), and our error is relatively low. 

What models are we thinking of why: For another model, we're thinking of doing specific transformations on each feature based on the distribution of the features or based on the feature's relationship to our y. If the relationship the feature has with our independent variable is more exponential, we may take the log of it to make it more linear. Additionally, if a feature seems more logarithmic relationship with our y, we may take the square of it to make it more linear. For example, let's say a country's GDP (x1) has an exponential relationship with the average lifespan (y), then we would do log(x1) or something similar to linearize. We will test to see which transformations result in the lowest MSE. Then we will perform linear regression on the transformed data, hopefully making our model more accurate and reducing the MSE and R2. Since we will be manually transforming our model to have a lower MSE, this will cause us to be at risk for overfitting. To avoid this, we will continue to perform K-Fold cross validation. 

# Conclusions for Model 1 and Model 2:
From training this first model, we've learned that (as we expected) the features do have an influence on life expectency, and that even with a simple linear model we can predict life expectancy fairly well. We want to increase the model complexity later on, and we will need to be careful of increasing it too much to the point of over-fitting, but we'll check for that :)
To improve our model, we will try feature transformations such as polynomial transformations and log transformations, since the relationship between features and life expectancy remains not fully determined after just one linear regression model.

For training the second model, we want to transform individual features based on the relationship each feature has with life expectancy. In our second model, we ended up squaring every single feature within a polynomial regression, but this may have caused some overfitting, so we hope to improve our model by slightly increasing the model complexity so that each feature can have a more linear relationship with the life expectancy feature we are trying to predict. We will do this by manipulating feautres in more complex ways, specific to each feature. As explained above, it is possible that some features may have a logarithmic relationship to the output, while others may have polynomial relationship. Doing these feature by features manipulations will allow us to create a model that more accurately captures the relationship between features and output, which is why we want to use this strategy to improve upon our second model. In addition, since right now we are using a lot of features, some of which intuitively might not have a relationship with the output, it may also be a good idea to perform dimensional reduction and get rid of some of the features, only keeping those that accurately represent the data. The motivation for this is mainly for the use of the model, as some of the features are difficult to collect in the real world.

# Final Report:

# Introduction
For our dataset, we chose to use a dataset from Kaggle that displays each country’s life expectancy, along with various features such as GDP, BMI, alcohol consumption, immunization coverage of certain diseases, etc. We chose this dataset because we wanted to predict a country’s life expectancy based on the other features. Having a good predictive model for this dataset would allow us to know which features have the most impact on life expectancy. This could have an impact on how people make decisions about their health in their everyday lives and could influence a country’s healthcare policies. 

# Methods
### Data Exploration
To explore our dataset we verified that there were no missing data or null observations in our dataset. Additionally we identified the datatypes of the features in our dataset and verified that they were all numerical except for one, ‘Country’, which was categorical. Additionally we observed that many of the features in our dataset are not normally distributed. 
<img src="images/Feature Distrubutions.png" alt="Coefficients" width="500"/>
### Preprocessing
We removed the categorical feature ‘Country’ from our datasets because we did not see it relevant for our model. We then decided to apply min-max normalization to our dataset because many of the features were not normally distributed, as noted in the Data Exploration section. Additionally we split our dataset into a training and test set with a 80:20 split.

### Model 1
For our first model we chose to do a linear regression model with a degree of 1. Our input matrix included the normalized features in our training set apart from ‘Life Expectancy’ which was used as the dependant feature. The features in our input matrix included "infant deaths", "Alcohol", "percentage expenditure", "Hepatitis B", "Measles", "BMI",  "under-five deaths", "Polio", "Total expenditure", "Diphtheria", "HIV/AIDS", "GDP", "Population", "thinness 1-19 years", "thinness 5-9 years", "Income composition of resources", "Schooling", "Year", "Status", "Life expectancy", "Adult Mortality". 

### Model 2
For our second model we chose to do a polynomial linear regression model with a degree 2. Our input matrix included the normalized features in our training set "infant deaths", "Alcohol", "percentage expenditure", "Hepatitis B", "Measles", "BMI",  "under-five deaths", "Polio", "Total expenditure", "Diphtheria", "HIV/AIDS", "GDP", "Population", "thinness 1-19 years", "thinness 5-9 years", "Income composition of resources", "Schooling", "Year", "Status", "Life expectancy", "Adult Mortality" as well as the square of the values from the previous features listed. In this step we also chose to increase the degree of the polynomial linear regression model to 3, which then added additional features in our features matrix that was the cube of the previous features listed. Our dependent feature was ‘Life Expectancy’.


# Results
### Model 1
For the results from our first linear regression model, we found that the mean squared error was fairly low for both the training data and the test data, with values of 0.0125 and 
0.0148 respectively. We also found that the r-squared values were 0.7246 and 0.6865 respectively. Additionally, here were our coefficients for the first model: 

<img src="images/Coefficients.png" alt="Coefficients" width="500"/>

These coefficients are for features: ["infant deaths", "Alcohol", "percentage expenditure", "Hepatitis B", "Measles", "BMI", "under-five deaths", "Polio", "Total expenditure", "Diphtheria", "HIV/AIDS", "GDP", "Population", "thinness 1-19 years", "thinness 5-9 years", "Income composition of resources", "Schooling", "Year", "Status", "Adult Mortality"]. Additionally, after performing k-fold cross validation for k = 5, we obtained these results for the mean squared error after each iteration:

<img src="images/KFoldModel1.png" alt="KFold" width="100"/>

Our average MSE was 0.0132. 

### Model 2
For the results of our polynomial regression model with degree two, we found that the train and test mean squared errors were 0.0102 and 0.0136 respectively. Additionally, we found that the r-squared values were 0.7752 and 0.7121, respectively. After performing k-fold cross validation for k = 5, we obtained these results for mean squared error after each iteration: 

<img src="images/KfoldModel2Poly2.png" alt="KFold" width="100"/>

Our average MSE was 0.0138.

For the results of our polynomial regression model with degree three, our mean squared errors for the train and test sets were 0.0019 and 2379.3295, respectively. Our r-squared values were 0.9582 and -50257.8120, respectively. After performing k-fold cross validation, we obtained these results for mean squared error after each iteration:

<img src="images/KFoldModel2Poly3.png" alt="KFold" width="300"/>

Our average MSE was 1645.2000. 

# Discussion
We began with a linear regression model in order to set a baseline for the relationships between our features and life expectancy. Linear regression models are simple and inferrable, allowing us to establish that baseline for when we are comparing more complex models. Our model performed well, achieving a training MSE of 0.0125 and a testing MSE of 0.0148. Using K-fold cross-validation, we saw consistent errors throughout the folds, hinting that our linear regression model generalizes well. We believed our results for our linear regression model align with our expectations. However, we suspected that we were underfitting the model due to the real life nature of our features and their non-linear relationships. Next, we tried polynomial regression. To address the issues like non-linear relationships in the previous model, we introduced polynomial features by squaring each input variable. We found that the second-degree polynomial model improved the results slightly, dropping the training MSE to 0.0102 and the testing MSE to 0.0136. We interpreted this shift to mean that the model was capturing more complexity than the linear regression without overfitting. This would have been the case hadn’t we shifted the polynomial degree to three. When we tried a third-degree polynomial model, our testing error exploded to 2379.33. We were very distraught by this outcome initially but, eventually chalked it up to overfitting. From this milestone we also learned that, when we squared our features, it treated them equally implying that every feature is equally as important when predicting life expectancy, which is not representative of their real life relationships. Although the second-degree polynomial model performed to our expectations, increasing the degree made us realize there is much more room for improvement. The overfitting was a sign that we needed better regularization and feature selection.  

# Conclusion
Overall we are fairly satisfied with how the project went, but we wish that we could have expanded to even more complicated models. We kept our model 1 and model 2 relatively simple as they were the first logical models to try for our dataset, and we found some meaningful results, experiencing overfitting when we were tuning our second model and discovering that we can actually make fairly accurate predictions based on just a linear combination of all of our features. As for future directions we would definitely want to get more models trained in general to see if we can do better than we already did. Since we just started learning about neural networks, it would be interesting to see how well they can make predictions about our data, and also we are curious to see how much a neural network model would tend to overfit compared to the overfitting that we experiences when tuning for our polynomial model. Unfortunately we don’t think we quite have the time to get this implemented due to our busy schedules, so that will have to be done later. Looking back on it, perhaps we should have dropped some of the features in out dataset when we did feature selection, as initially we chose as many features as possible so that if a relationship exists, we would find it, but there are clearly features whose correlation with life expectancy is much higher than others. In summary, while our project demonstrated promising results and provided valuable insights, there is still ample room for improvement and exploration, particularly with more advanced models and refined feature selection methods.

# Statement of Collaboration
During this project, we had a meeting for each milestone where we all got to work at the same time until the milestone was done! That’s why we aren’t really sure what to give for the titles, since we all sort of did every aspect of the project, we rotated and got slightly different parts done each milestone, but we all worked together at the same time. We all coordinated on discord when we would meet.

Name: Annie Ping 	Title: Meetings leader, Codewriter, Writer	
Contribution: Write up for two of the milestones, code for training our second model, ¼ of this final report

Name: Sierra Myers	Title: Codewriter,  Writer
	Contribution: Write up for one of our milestones, code for training our first model, ¼ of this final report

Name: Taylin Kieu	Title: Codewriter, Writer 
	Contribution: Write up for one of our milestones, code for making a fitting graph for our models, ¼ of this final report

Name: Liam Hardy	Title: Codewriter, Writer
	Contribution: Write up for one and a half of the milestones, one fully and the other adding on after someone else's. Code for K-fold cross validation and cleaning up all of our code

