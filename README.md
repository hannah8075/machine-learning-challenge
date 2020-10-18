# machine-learning-challenge
## Background
Over a period of nine years in deep space, the NASA Kepler space telescope has been out on a planet-hunting mission to discover hidden planets outside of our solar system.

To help process this data, I created machine learning models capable of classifying candidate exoplanets from the raw dataset.

## Preprocess the Data
- Preprocess the dataset prior to fitting the model.
- Perform feature selection and remove unnecessary features.
- Use MinMaxScaler to scale the numerical data.
- Separate the data into training and testing data.


## Tune Model Parameters
- Use GridSearch to tune model parameters. 
- Tune and compare at least two different classifiers.

## Analysis
- For both models, I loaded in the data using a csv file from Kaggle (https://www.kaggle.com/nasa/kepler-exoplanet-search-results). 
- Instead of removing columns and rows with NAN values, I imputed the mean to fill in the NAN values. 
- For variables where imputing mean was not feasible, I removed them. I also removed variables that were string type. 
- There were 41 remaining variables. 
- I then split the data into test and train as well as scaled the variables.

### Model 1: SVM
- using the SVM model, the score was 0.8568. 
- I used the GridSearchCV to tune the model's parameter and found that the best parameters for the dataset was {'C': 50, 'gamma': 0.0001}.
- using the tuned model, the score slightly improved to 0.8745. 

### Model 2: Random Forest
- using the random forest model, the accuracy was 0.8948.
- I then ranked the features by their importance and only kept features that had scores > 0.01, resulting in 30 features.
- using these selected features, the accuracy improved very slightly to 0.8993.
- I then used the GridSearchCV to tune the model and found the best parameters to be {'criterion': 'gini', 'max_depth': 9, 'max_features': 'auto', 'n_estimators': 200}.
- Using these parameters, the score did not improve (0.8944). 

Between these two models, randrom forest performed better than SVM. Additionally, tuning the models only helped improve the model slightly. Overall, the models seem to do a fair job of predicting new exoplanets. However, the model would be better if there the data was more complete so that imputed means didn't have to be used. 

