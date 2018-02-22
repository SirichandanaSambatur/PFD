# Machine Learning Engineer Nanodegree Capstone Proposal
## Predicting flight delays using supervised learning

### Problem Statement:

The objective of this project is to build an efficient and generalized model that predicts flight delays. Machine Learning algorithms have the ability of understanding and detecting patterns in the historical data. Some of the machine learning algorithms such as Support Vector Machines, Logistic Regression, Decision Trees etc. can be used to learn the patterns of flight delays and build an effective predictive model. The project considers this problem as a classification problem and builds an identifier that predicts whether the departure time of the flight will be ‘on-time’ or ‘delayed’. The input for these models will be a data instance that represents the information about a flight. This information includes airline carrier, origin airport, scheduled departure time, destination airport, scheduled arrival time etc. Provided an unlabelled instance which represents a flight, the trained models will identify if the flight will depart on-time or not.

### Results
Model Evaluation:
The data for the months of January and February have been selected for modeling. All the classifiers have been trained on about 80% of the data which represent the flights’ information until February 15, 2015. The trained classifiers have then been tested on the remaining data which represents the information about flights after February 15th, 2015 and constitute about 20% of the data chosen for modeling. The performance measures listed in the table above have been recorded by testing the classifiers on the unseen testing data.
Predicting flight delays is a binary classification problem and the most suitable metric for evaluating binary classifiers is the area under ROC. The final Decision Tree model trained by
 11
using ‘gini index’ as the splitting criteria and a minimum samples split of 20 had an accuracy of 53.11 and an area under ROC of 0.58. The splitter method used for this model is ‘best’ i.e. the attribute resulting in best split is always chosen rather than a random approach.


After several iterations of training the Random Forest classifier with different parameter settings, the final model used 200 estimators and a minimum samples split of 40. The criteria used for determining the best split is ‘entropy’ which calculates the information gain. 
The Random Forest classifier did not employ any pruning techniques for the trees and every tree is expanded until its maximum depth. This condition is facilitated by setting the value of the parameter ‘max_depth’ to ‘None’. The number of features considered while determining the best split is the square root of the number of features supplied. This condition is facilitated by setting the value of the parameter ‘max_features’ to ‘auto. This model had an accuracy of 55% and an area under the ROC of 0.67 which is better than that of the other classifiers.
As the data set is time series, and suffers from look-ahead bias, which means when the data is trained on future data and tested on past data, it would lead to inaccurate results. 

Hence, for data sets like this cross validation techniques cannot be applied. So, to check for the robustness of our final Random Forest classifier, it has been applied on instances from March 1, 2015, to March 10, 2015 which is considered as our validation set. This dataset is completely new and independent of the training and testing sets. The features of this validation set have also been transformed by using the previously fitted SelectKBest transformer. The final Random Forest model preformed very well in predicting the flight status on the validation set. The final model had an accuracy of 64.16%, a precision score of 0.7, a recall score of 0.75 and an area under the ROC of 0.65. These metrics indicate that the performance of the final model on this independent dataset is efficient and also beats the benchmark model and other classifiers. Considering this the Random Forest classifier has been chosen as the final model as it is robust on unseen data.

### Conclusion
Free-form visualization:
One of the most important aspects of building an efficient model is to identify the best features that represent the information about data. For this project, Feature Selection has been used to reduce the size of the feature space and to identify the best features. The following figure displays the best 50 features.
It can be noticed that the most important feature is ‘DAY_OF_WEEK_Sat’ which indicates of the day is a Saturday. This observation is interesting because the analysis during the exploratory visualization phase did not indicate any strong relationship between the Day of the week and the light status. From the other best
features most of the features represent information about the origin airport. In the real world this aspect of flights is very important because some of the major airports in the United States have a lot of air traffic and this could be a reason for delayed flights.
