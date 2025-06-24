* Basic Understanding of Data
* EDA
* Feature Engineering
* Data Preprocessing
* Model Building
* Model Performance Check
* Model Hyperparameter tuning
* Stacking HyperTuned Models
* Predicting test csv using stacked model
* Creating a csv file

# Importing Libraries
#### Import All Libraries which are required for coding.

# Basic Understanding of Data
`` df.shape ``<br>
`` df.head()``<br>
`` df.info()``<br>
``df_duplicated.sum()``<br>
``df.dtypes``
``df1 = (train_df.isnull().sum()[train_df.isnull().sum()>0]).to_frame().rename(columns={0:"Number of Missing values"})``
``train_df.select_dtypes(include="object").nunique())``

# EDA

* Visualise Target feature distribution using 
piechart
* Use histplot for numerical distributions like Age
* Visualise single/multiple numerical distributions using histplot
* Visualise single/multiple categorical distributions using countplot.
* Use boxplots for outliers

# Feature Engineering
* Create new features based on existing features
* Perform EDA on new features

# Data Preprocessing
* Handle Missing Values using SimpleImputer for <br> 
a) Categorical-Strategy="Most Frequent" <br>
b) Numerical-Strategy="Median/Mean"

* Drop Categorical features with high cardinality
* Apply log transformation if the numerical features are skewed
* Check data-Type of features
* Feature Encoding <br>
a)One Hot Encoding for nominal<br>
b)Labelencoding for categorical<br>
* Select features and labels for model training
* Do feature scaling
* Splitting data both for scaled and non scaled

# Model Building 
* Perform accuracy score of multiple models
* Do hyperparameter tuning for Selected Models
* Stack the models with best hyperparameters

# Predict the test file with stacked model 