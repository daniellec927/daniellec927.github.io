---
layout: page
title: 2026 March Madness Prediction
description: ML model that predicts the outcome of NCAA Men's and Women's March Madness basketball tournament games
img: #assets/img/1.jpg # swap for your own thumbnail placed in assets/img/
importance: 1 # lower number sorts earlier within the category
category: projects # must match one of `display_categories` in _pages/projects.md
redirect: #https://github.com/daniellec927/march-madness-predictions   # uncomment to link the card straight to an external page
---

A structure that works well for data science:

1. **Problem**

As the 2026 NCAA March Madness approaches, it seemed relevant to cover it by participating in the March Madness prediction. The primary goal was to build a model that predicts the winning probability for every possible match among the participating teams, applicable to any year, provided the data is secure. While all the data up to the 2026 regular seasons were provided, the actual 2026 March Madness result to evaluate the model’s performance was not provided. So, the model's accuracy was tested using data from the recent seasons.

The goal was to explore whether the neural network can capture patterns in historical trends to successfully predict competition results, especially given the noisy, high-variance data. I expected the project to demonstrate the application of neural networks to real-world decision-making, as they are better at handling data with multiple features and nonlinear relationships than simple statistical models. Rather than binary results, probabilities were predicted, so the model can avoid potential “gray areas” and account for the confidence level of each prediction.

This ML model can further be used for sports analytics or sports betting, as they require specific outcomes more than simple binary results.  

<hr>

2. **Data**

The data integrates both women’s and men’s data into a single dataset, allowing exploration of general patterns regardless of gender. The dataset has five sections: 

    (1) Basics

    (2) Team Box Scores

    (3) Geography

    (4) Public Rankings

    (5) Supplements

These include team information, tournament seeds, game-by-game statistics at a team level, and so on. The dataset was appropriate for testing our research question, as it provides large-scale data from 1985 that is necessary to train a neural network to identify hidden patterns or nonlinear relationships. 

The data was provided from Kaggle, through the Kaggle competition.

It was up to personal judgment on whether to use a certain dataset or not. 

<hr>

3. **Approach**

With the data, I first conducted an Exploratory Data Analysis (EDA). This step was necessary to visualize the data for linear patterns and to understand the dataset as a whole. In particular, the bar graph and heatmap were helpful for seeing which features had the most significant impact on the winning probability.

The initial inputs had 47 features, including all numerical data we could use. I also tried an advanced input set, in which I performed feature engineering and feature elimination. The feature engineering process involved mathematical calculations to quantify differences in statistics between competing teams. Then, I reduced the features to 10 by combining many data points into a single feature that more accurately captures the differences. It was done for model simplicity and increasing speed. The output was the winning probability for a specific team in a matchup, expressed as a continuous value between 0.0 and 1.0.

For the model, I split the dataset into three sections: training (80%), validation (10%), and testing (10%). To prevent data leakage and ensure the model can actually predict the future, I split the data chronologically rather than randomly shuffling, to prevent future data used to predict the outcome from the past. The training set was used to train the model and tune hyperparameters, and the validation set to compare results across all the methods we experimented with. The testing data set was for evaluating the performance of the final chosen method. 

This project was done as an experiment format, comparing various neural network models and their performances.

    (0.5) Baseline model - Team with higher seed ALWAYS wins
    (1) Linear baseline model - Logistic Regression
    (2) MLP Regressor model 
    (3) MLP Regressor model with hyperparameter tuning (with GridSearchCV)
    (4) MLP Regressor model with Ensemble method
    (5) Blended model (MLP Regressor model 90% + Linear Regression model 10%)

![Blended model architecture](assets/img/march-madness-model-architecture.png)

4. **Results**

Validation set

| method | Log Loss | ROC-AUC | Accuracy | Brier Score
| --- | --- | --- | --- | --- |
| 0.5 | 8.5742 | 0.7437 | 0.7516 | 0.2486 |
|1 | 0.5338 |0.8154 | 0.7225 | 0.1814 |
|2 | 0.5222 | 0.8172 | 0.7360 | 0.1754 |
|3 | 0.5122 | 0.8328 | 0.7476 | 0.1678 |
|4 | 0.5113 | 0.8282 | 0.7341 | 0.1695 |
|5 | 0.5005 | 0.8329 | 0.7495 | 0.1677 |

The final model, the blended model of MLP and Logistic Regression, had a similar result for the validation data metrics (log loss: ~0.501, ROC: ~0.833, Acc: ~0.750, Brier: ~0.168) and the test data metrics (log loss: ~0.494, ROC: ~0.829, Acc: ~0.754, Brier: ~0.168). This implies that the model was not overfitting and did a good generalization. Additionally, advanced features, ensemble model, and the blending model did improve the model prediction ability. 

5. **Links**

link to repo: https://github.com/daniellec927/march-madness-predictions
