## SpaceX Falcon9 Predictive Landing With A Logistical Regression Model

# Introduction
One of the greatest technological feats of our time is the creation and development of reusable rocketry. In particular, the SpaceX Falcon 9 rocket kickstarted an era of reduced expenses in space flight, leading to more efficient travel and the beginning of a new era of scientific exploration. For some more in depth points, I love this LinkedIn article: 

https://www.linkedin.com/pulse/next-generation-rockets-exploring-reusability-cost-efficiency/

Inspired by my love for space exploration and big data, I sourced SpaceX's reusable Falcon 9 rocket for the basis of this project. In this project, I used a logistical regression model to see if I could accurately predict the success of Falcon 9 booster landings using data such as payload mass, amount of flights of the booster, whether it was reused or not, and how far it flew. Note that the dataset used only included landings from 2013 to 2020. Nowadays, the Falcon 9 rocket has become uber-successfull, boasting a total success percentage of 96.2% (dating before 2013). But, a majority of these landings have taken place post-2022, as SpaceX partnered with Nasa for ISS/Deployment/General operations. 


# Why Logistical Regression?
There are many reasons why I chose logistic regression for my model, including:

1. The "Successful / Unsuccesful" nature of the outcomes is binary.
2. Logistic Regression provides a clear interpretation of the relationship between the independent variables and the log-odds of the target variable. The coefficients in          logistic regression represent the log-odds ratio.
3. Logistic Regression tends to have lower variance compared to more complex models, making it less prone to overfitting. Since the dataset wasn't big, logistical          regression was a good fit.
4. It is efficient.
5. Logistic Regression allows you to interpret the importance of different features based on their coefficients. For this reason, it helped me see which parameters were more      impactful for the outcome which was great from a learning perspective.
6. Etc.


# Use of Cross-Validation

In my model, I used K-fold cross-validation using 10 folds. Meaning, in the program, a GridSearchCV object is instantiated with the parameter cv = 10. This means that the dataset is split into 10 folds, and the logistic regression model is trained and evaluated 10 times. Each time, a different fold is used as the validation set, and the remaining folds are used as the training set. Additionally, since refit = True, after the cross-validation process, the GridSearchCV object will refit the logistic regression model using the best hyperparameters on the entire training dataset. This ensures that the final model is trained on as much data as possible before making predictions on new, unseen data. As for the benefits to this, the use of k-fold cross-validation helps provide a more robust estimate of the model's performance by averaging the performance metrics over multiple train-test splits.

# Confusion Matrix

In this project, I created a confusion matrix to evaluate the strength of my model. I would like to thank Kelli Belcher (https://www.kaggle.com/kellibelcher) for the implementation of it. The matrix provides great insight to the stregnth of the model outside of the % accuracy.

# Results

After testing and tuning of the model, I was able to achieve an accuracy of 83% on predicting the success of landings. Although it wasn't perfect, for the simplicity of the model, I consider it a huge success. While this number is not great in the perspective of multi-million dollar launches (that could contain humans on board in the future!), it is very high considering the randomness of these complex rockets.


# Thanks
I would like to again thank Kelli Belcher and her article "https://www.kaggle.com/code/kellibelcher/spacex-rocket-landing-predictive-analysis/notebook" for guidance in this project. I really enjoyed seeing how our models compared, and how she implemented more advanced models to further the success of prediction. 
