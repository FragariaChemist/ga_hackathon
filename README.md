# ![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png) Hackathon:  Predicting Global Video Games Sales Using Linear Regression

## The Ideal
I want to predict global sales of video games using Kaggle's Video Game Sales with Rankings dataset.  Features used are:

* Platform
* Genre
* Year of Release
* Publisher
* Developer
* Rating
* User/Critic Ratings and Counts

Sales are millions of units sold worldwide


## The Reality

My biggest challenge was getting a column transformer to work.  I wanted to tranform both numerical and categorical features in different ways, but putting everything in a column transformer was throwing errors.  This sklearn documentation directly address the kind of feature engineering I wanted to perform: [Column Transformer with Mixed Types](https://scikit-learn.org/stable/auto_examples/compose/plot_column_transformer_mixed_types.html)

The name and invididual sales columns were dropped.  Having the name of each game would not help a model and the individual sales all add up to global sales.  Numerical features were imputed with average values and then scaled.  Categorical features were imputed with most frequent values and one hot encoded.

Three regression models were constructed - linear, ridge, and lasso.  The best of the three was Lasso, though none were significantly better than the others.  Average train R2 value was 0.38 with Lasso at 0.33.  Training R2 was about 0.19 for all three models.

Lastly I tried a basic linear regression with just the Platform and Genre features.  This did much worse - training R2 was 0.05 and testing R2 was 0.009.

It seems like scores could be a good indicator of how well a game sells, but there is a lot of missing data in these features.  The span of time in this set is large and games sold in the 1980s are not the same prices as they are in 2016.  This may skew the model.  

## What Could Be Better

Given time, it wouldn't be difficult to fill out some of the features of the dataset and not impute them.  Data such as release date, platform, genre, publisher, etc. should be easy to find.  This data is also due for an update; the latest games are from 2016.
