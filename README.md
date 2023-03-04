# Plant Nutrition Prediction with Supervised Machine Learning

This project aims to built a Webapps to predict plant nutrition with 8 variable 

# File Explanation on Github

This repository consists of several files, namely :

- Folder `deployment` = Contains files used for *deployment* to `HuggingFace` (contains models, python applications etc.)
- `aria_ftds_rmt17_evan_derin_ihsanudin.ipynb` = This file is the main *notebook* used to explore dataset and built model
- `inferencing_aria_ftds_rmt17_evan_derin_ihsanudin.ipynb`= *Notebook* used for *testing inference*. Inferencing is done on a separate *notebook* to prove that the model can run on a *notebook* that is *clean* of variables
- `url.txt` = Deployment URL to HuggingFace

# Brief Summary of Project

The flow of this *project*, first EDA (*Exploratory Data Analysis*) to find out the basic picture of the *dataset*. Second, *cleaning* and *preprocessing* of the *dataset*. From *preprocessing* I drop the *feature* `sample_type` because it does not affect the regression. Third, built and compare evaluation of 8 Model (Linear Regression, KNN, Bayesian Ridge, Support Vector Machine, Decision Tree, Random Forest, XGBoost & ADABoost) and choose Random Forest as Best Model, then improve this model using GridsearchCV. Result of the model shows MAE 0.05 on train-set and MAE 0.12 on test-set

# Project Conclusion
  
Strength
    
1. Has MAE 0.12
2. This model is resistant to *outliers*
3. This model has a small bias because there is already *rules* for the regression

Weaknesses
    
1. Cannot predict outside the data *range*, because it uses a random forest algorithm
2. Time for *testing* and *training* is quite long because it uses bagging algorithm
3. Difficult to interpret why the model can predict plant nutrients to that number (different from linear regression which is easy to interpret)