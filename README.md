# Recommendation-system

## Training Model.ipynb
+ This project is used to build a model for recommending 10 products that are likely to be interacted by each of 22,000 customers from over 14,000 types of products.
+ The project includes two types of models, MF (Matrix Factorization) and NeuMF (Neural Matrix Factorization), to be used for the recommendation system.
+ After the model is trained, some functions will be used to evaluate the model's performance such as mean_precision_recall_at_k, average_ndcg, and hit_rate.

## Negative Processing.ipynb
+ As the sample for this recommendation system only includes the history of products that customers have purchased, it is difficult to determine the level of interaction between customers and products.
+ Therefore, this project will use Negative Sampling, which is commonly used for Implicit Feedback in recommendations.
+ Thus, the training samples will include two labels: 1 (products that customers have purchased in the past) and 0 (products that customers have never purchased).
+ The method of negative sampling mentioned in this file is based on the interaction score of customers with that product.
+ The sampling mechanism involves creating one training sample using random sampling to create negative samples (called sample 1) and using this sample for Training Model.ipynb.
+ After training, this sample will be used to predict scores for 14,000 products for each customer.
+ The products with the highest scores will be used for sample 2, with the purpose of helping the model distinguish which products the user has interacted with and which products are likely to be interacted with.
+ There are two sections of code for creating negative samples because in the first section, the model will predict scores for all 14,000 products and select a number of negative samples with the highest scores that do not overlap with the products the customer has purchased. This process takes a lot of time to create samples (more than 6 hours), so the second sample creation code randomly selects a number of products from the 14,000 products to put into the model and predict scores. This helps to reduce the time to create samples to 2 hours.
+ After that, the samples will be put into a csv file and put into Training Model.ipynb to proceed with training.
