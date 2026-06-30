# Predicting Sephora Product Ratings 🛍️
## Introduction
Imagine scrolling through hundreds of products on the Sephora website–each offering different advantages while being at contrasting price points. When it comes to beauty and skincare, obtaining accurate insights on whether a product is right for individual interests and skin types is invaluable. “Which of these is right for me? Which product is truly worth spending on?” These are questions I often ask myself when looking for a new product to purchase, even with any other online retailer.

Fortunately for shoppers, like myself, knowing that consumers with similar product preferences have already tried and purchased the item makes all the difference in making the right purchasing decision. In moments like these, relying on user ratings and reviews provides promising reassurance in making the best choice.

I noticed that a product rating on the Sephora website only consists of 5 stars that are filled accordingly on a continuous scale of 1 to 5 (lowest to highest). I started to wonder, “What exactly drives a user to give a product a high or low rating?” I realized there are numerous factors that could impact this even beyond the product’s performance like its brand, popularity, and even whether or not it is an exclusive item.

I would like to predict how a rating is determined by users based on these characteristics and to uncover trends or patterns from Sephora product ratings. By understanding how product factors contribute to high or low ratings, we can be better informed on shopper decision making.

## Dataset
The dataset that I am using for the project was found on Kaggle, “Sephora Products and Skincare Reviews.” It consists of information on over 8,000 products from the Sephora online store, and was scraped by Nady Inky via Python scraper in March 2023.

## Methodology
### Data Cleaning & Exploratory Data Analysis (EDA) 📊
Let's start by tidying and exploring the raw data. Our dataset has quite a bit of missing values! There is missing data for 14 of the 27 predictors. 

I will examine if there is a pattern of missingness between variables. What’s notable in the missing data plot is `rating` and `reviews`. There is 3.27% of data for the response variable, `rating`, that is missing, and we can see that this same percent is missing for `reviews`.

While 19.3% of the data is missing, 80.7% is present and we can still use that for our EDA process.

To understand the data further, I conducted visual EDA. This included
- distribution of response variable `rating`
- variable correlation plot (correlation  matrix of numeric variables to determine relationship)
- `product prices`:  I expect that products with lower prices may have a higher rating as they are more affordable. This is because cheaper products can be perceived to offer good value for the price paid, especially when it performs better than expected for that price point.
-  box plot: measuring correlation with Sephora Exclusive products and `rating`.
To view more visualations I conducted, you can take a look at my full report under "Visual Exploratory Data Analysis" 
 
## Model Building and Process ⚙️
Now that we have a better understanding of our dataset, we can start setting up our models to predict product ratings! We need to split our data into training and testing data, create our recipe, and perform cross validation.

I decided to use 0.7 as the proportion for the split so that there is a significant amount of training data to help the model predict accurate results. This will help with reducing overfitting and improve the model’s performance on the testing data. It is also important to set a seed so that we can reproduce our results.

Now we can finally start building our models. The model building process consists of these steps. For this project, I have decided to fit 6 models: 

### Linear Regression, K Nearest Neighbors, Elastic Net Linear Regression, Decision Tree, Random Forest, and Boosted Trees.

To access the performance of all our models, I decided to choose Root Mean Squared Error (RMSE) as the metric. Lower values of RMSE indicate a better predictive accuracy.

## Model Results 📈
The top 3 models with the lowest RMSE values are: Random Forest, Boosted Trees, Decision Tree. We can visualize these, and you can view it in the full report under "Visualizing Model Performance"!

We determined that the best performing model on our folds with the lowest RMSE was the best fit for predicting Sephora product ratings. We should see which specific parameters were best for this random forest model. And the best model is… Random Forest Model #48! This was the specific random forest model that fit our data best, with an RMSE value of 0.4786, 50 trees, 4 predictors, and a minimum node size of 12.

After fitting to the training and testing data, Compared to the value of 0.4785896 from the folds, the random forest model did slightly worse but not by a large value! The two RMSE values are fairly close and the difference is around 0.001. Not bad! The estimate is also acceptable when we consider the range of our outcome variable, `rating`, which is from 1 to 5.

## Analyzing Variable Importance 🥽
Using a random forest model, I created a variable importance plot to identify top predictors:
- reviews
- loves_count (count of how many 'likes' a product receives)
- price_usd

Like expected, reviews plays a large role in predicting rating! This makes sense as generally products with more reviews might have more balanced ratings, making it useful in predicting rating. There may be a consistent relationship between reviews and ratings in the training dataset for the Random Forest model. The second highest variable, loves_count, is also a significant predictor. Similarly to reviews, the higher number of “loves” for a particular product may be a good indicator to our model of what a rating may be. Price, the third highest variable of importance, also is reasonable as it can influence consumer expectations when shopping. Consumers may rate products more highly when an expensive item meets their expectations whereas if a product is overpriced, its rating may be lower.

## Results & Next Steps 🎯

I determined that the best performing model to predict a product’s rating from the Sephora dataset is the random forest model.
One way to improve model performance may be to incorporate and consider other variables such as: 
- number of sales a particular product has received in the past year
- how long the product has been sold at Sephora
- whether or not the item is considered a ‘bestseller.’

This project has not only enhanced my knowledge on machine learning techniques–it also broadened my perspective on how such insights can have significant implications in business contexts! I’ve also found myself more interested in understanding the reasoning behind why a certain model may perform better than others and how the features specific to my dataset can contribute to this. Although the random forest model did not perfectly predict the rating of a Sephora product, this project has been a valuable opportunity to apply machine learning methods to real world data.

## Full Project Report: 
https://sarahllew.github.io/Predicting_Sephora_ML.html
