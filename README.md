An analysis using Machine Learning algorithms to identify credit card risk using a dataset from LendingClub.

# Overview

The purpose of this analysis is to understand how to utilize `Machine Learning` statistical algorithms to make predictions based on data patterns provided. In this challenge, we focus on **Supervised Learning** using a free dataset from **LendingClub**, a P2P lending service company to evaluate and predict credit risk. This reason why this is called **"Supervised Learning"** is because the data includes a labeled outcome. 

To complete this analysis, we use different `Machine Learning` techniques to train and evaluate the data with unbalanced classes. The dataset from the **LendingClub** has an unbalanced classification problem due to the number of good loans outweighing the amount of risky loans. In order balance out the classifications to allow for more meaningful predictions and improve the accuracy score, we needed to employ various `Machine Learning` algorithms to resample the data. These algorithms include `RandomOverSampler`, `SMOTE`, `ClusterCentroids`, `SMOTEENN`, `BalancedRandomForestClassifier`, and `EasyEnsembleClassifier`.

# Results

As mentioned in the overview, we use `Machine Learning` to resample the dataset using `Python` libraries: `scikit-learn` and `imbalanced-learn` evaluate the results and provide a comparison for our analysis. 

The original dataset contained 115,675 loan applications in Q1 of 2019. We used the "loan status" to determine whether the application was considered "low" or "high" risk. Applications that had "current" as the "loan status" were classified as "low risk" and the remaining as "high risk". This reduced the dataset to 68,817 total applications with 99% classified as "low risk". 

![datacount](https://github.com/tianiedwards98/Credit_Risk_Analysis/blob/main/Resources/Deliverable-1/Screen%20Shot%202023-02-21%20at%207.17.43%20PM.png?raw=true)

Using the 75/25% method to split the data for training vs. testing, 51,366 "low risk" and 246 "high risk" applications were categorized into the training set.   

![trainingdata](https://github.com/tianiedwards98/Credit_Risk_Analysis/blob/main/Resources/Deliverable-1/Screen%20Shot%202023-02-21%20at%206.48.29%20PM.png?raw=true)

## Deliverable 1: Use Resampling Models to Predict Credit Risk

### Oversampling

**`RandomOverSampler Model`** randomly selects from the minority class and adds it to the training set until both classifications are equal. The results classified 51,366 records each as High Risk and Low Risk.

![oversamplecount](https://github.com/tianiedwards98/Credit_Risk_Analysis/blob/main/Resources/Deliverable-2/oversampling/Screen%20Shot%202023-02-21%20at%207.10.54%20PM.png?raw=true)

  * Balanced accuracy score: 66%.

  ![oversampleacc](https://github.com/tianiedwards98/Credit_Risk_Analysis/blob/main/Resources/Deliverable-2/oversampling/Screen%20Shot%202023-02-21%20at%207.11.01%20PM.png?raw=true)

  * The "High Risk" precision rate was only 1% with the recall at 72% giving this model an F1 score of 2%.
  * "Low Risk" had a precision rate of 100% and recall at 60%.  
  
  ![oversamplecm](https://github.com/tianiedwards98/Credit_Risk_Analysis/blob/main/Resources/Deliverable-2/oversampling/Screen%20Shot%202023-02-21%20at%207.11.06%20PM.png?raw=true)
  
  ![oversampleclass](https://github.com/tianiedwards98/Credit_Risk_Analysis/blob/main/Resources/Deliverable-2/oversampling/Screen%20Shot%202023-02-21%20at%207.11.12%20PM.png?raw=true)

**`SMOTE (Synthetic Minority Oversampling Technique) Model`**, like `RandomOverSampler` increases the size of the minority class by creating new values based on the value of the closest neighbors to the minority class instead of random selection. 

  * The balanced accuracy score improved slightly to 65.1%.

  ![smoteacc](https://github.com/tianiedwards98/Credit_Risk_Analysis/blob/main/Resources/Deliverable-2/oversampling/SMOTE/Screen%20Shot%202023-02-21%20at%207.12.54%20PM.png?raw=true)

  * Like `RandomOverSampler`, the "High Risk" precision rate again was only 1% with the recall degraded to 61% giving this model an F1 score of 2%.
  * "Low Risk" had a precision rate of 100% and an improved recall at 69%.  

  ![smotecm](https://github.com/tianiedwards98/Credit_Risk_Analysis/blob/main/Resources/Deliverable-2/oversampling/SMOTE/Screen%20Shot%202023-02-21%20at%207.13.00%20PM.png?raw=true)
  
  ![smoteclass](https://github.com/tianiedwards98/Credit_Risk_Analysis/blob/main/Resources/Deliverable-2/oversampling/SMOTE/Screen%20Shot%202023-02-21%20at%207.13.06%20PM.png?raw=true)

### Undersampling

**`ClusterCentroids Model`**, an algorithm that identifies clusters of the majority class to generate synthetic data points that are representative of the clusters. The model classified 246 records each as High Risk and Low Risk.

![undersamplecount](https://github.com/tianiedwards98/Credit_Risk_Analysis/blob/main/Resources/Deliverable-2/undersampling/Screen%20Shot%202023-02-21%20at%207.13.37%20PM.png?raw=true)

  * Balanced accuracy score was lower than the oversampling models at 54.5%.

  ![underacc](https://github.com/tianiedwards98/Credit_Risk_Analysis/blob/main/Resources/Deliverable-2/undersampling/Screen%20Shot%202023-02-21%20at%207.13.48%20PM.png?raw=true)

  * The "High Risk" precision rate again was only at 1% with the recall at 69% giving this model an F1 score of 1%.
  * "Low Risk" had a precision rate of 100% and with a lower recall at 40% compared to the oversampling models.  

  ![undercm](https://github.com/tianiedwards98/Credit_Risk_Analysis/blob/main/Resources/Deliverable-2/undersampling/Screen%20Shot%202023-02-21%20at%207.13.55%20PM.png?raw=true)
  
  ![underclass](https://github.com/tianiedwards98/Credit_Risk_Analysis/blob/main/Resources/Deliverable-2/undersampling/Screen%20Shot%202023-02-21%20at%207.14.02%20PM.png?raw=true)

## Deliverable 2: Use the SMOTEENN algorithm to Predict Credit Risk

### Combination Sampling

**`SMOTEENN (Synthetic Minority Oversampling Technique + Edited NearestNeighbors) Model`** combines aspects of both oversampling and undersampling. The model classified 68,460 records as High Risk and 62,011 as Low Risk.

![SMOTEENNcount](https://github.com/tianiedwards98/Credit_Risk_Analysis/blob/main/Resources/Deliverable-2/combo-sampling/Screen%20Shot%202023-02-21%20at%207.14.56%20PM.png?raw=true)

  * The balanced accuracy score improved to 64.5% when using a combined sampling model.

  ![SMOTEENNacc](https://github.com/tianiedwards98/Credit_Risk_Analysis/blob/main/Resources/Deliverable-2/combo-sampling/Screen%20Shot%202023-02-21%20at%207.15.03%20PM.png?raw=true)

  * The "High Risk" precision rate did not improve was only 1%, however the recall increased to 72% giving this model an F1 score of 2%.
  * "Low Risk" still showed a precision rate of 100% with the recall at 57%.  
  
  ![SMOTEENNcm](https://github.com/tianiedwards98/Credit_Risk_Analysis/blob/main/Resources/Deliverable-2/combo-sampling/Screen%20Shot%202023-02-21%20at%207.15.09%20PM.png?raw=true)

  ![SMOTEENNclass](https://github.com/tianiedwards98/Credit_Risk_Analysis/blob/main/Resources/Deliverable-2/combo-sampling/Screen%20Shot%202023-02-21%20at%207.15.15%20PM.png?raw=true)

## Deliverable 3: Use Ensemble Classifiers to Predict Credit Risk

Compare two new `Machine Learning` models that reduce bias to predict credit risk. The models classified 51,366 as High Risk and 246 as Low Risk.

![Balancedcount](https://github.com/tianiedwards98/Credit_Risk_Analysis/blob/main/Resources/Deliverable-3/Screen%20Shot%202023-02-21%20at%206.56.15%20PM.png?raw=true)

**`BalancedRandomForestClassifier Model`**, two trees of the same size and equal size to the minority class are constructed to represent one for the majority class and one for the minority class. 

  * The balanced accuracy score increased to 78.9% for this model.

  ![balanceacc](https://github.com/tianiedwards98/Credit_Risk_Analysis/blob/main/Resources/Deliverable-3/Screen%20Shot%202023-02-21%20at%206.56.26%20PM.png?raw=true)

  * The "High Risk precision rate increased to 3% with the recall at 70% giving this model an F1 score of 6%.
  * "Low Risk" still had a precision rate of 100% with the recall at 87%.  
  * The top feature by importance was "total_rec_prncp" at 7.9% of the total.

  ![balancecm](https://github.com/tianiedwards98/Credit_Risk_Analysis/blob/main/Resources/Deliverable-3/Screen%20Shot%202023-02-21%20at%206.56.37%20PM.png?raw=true)
  
  ![balanceclass](https://github.com/tianiedwards98/Credit_Risk_Analysis/blob/main/Resources/Deliverable-3/Screen%20Shot%202023-02-21%20at%206.56.44%20PM.png?raw=true)

  ![balancefeature](https://github.com/tianiedwards98/Credit_Risk_Analysis/blob/main/Resources/Deliverable-3/Screen%20Shot%202023-02-21%20at%207.29.22%20PM.png?raw=true) 

**`EasyEnsembleClassifier Model`**, a set of classifiers where individual decisions are combined to classify new examples.

  * The balanced accuracy score increased to 93.2% with this model.

  ![easyeacc](https://github.com/tianiedwards98/Credit_Risk_Analysis/blob/main/Resources/Deliverable-3/Screen%20Shot%202023-02-21%20at%206.57.03%20PM.png?raw=true)

  * The "High Risk precision rate increased to 9% with the recall at 92% giving this model an F1 score of 16%.
  * "Low Risk" still had a precision rate of 100% with the recall now at 94%.  

  ![easycm](https://github.com/tianiedwards98/Credit_Risk_Analysis/blob/main/Resources/Deliverable-3/Screen%20Shot%202023-02-21%20at%206.57.11%20PM.png?raw=true)
  
  ![easyclass](https://github.com/tianiedwards98/Credit_Risk_Analysis/blob/main/Resources/Deliverable-3/Screen%20Shot%202023-02-21%20at%206.57.16%20PM.png?raw=true)

# Summary

In reviewing all six models, the `EasyEnsembleClassifer` model yielded the best results with an accuracy rate of 93.2% and a 9% precision rate when predicting "High Risk candidates. The sensitivity rate (aka recall) was also the highest at 92% compared to the other models. The result for predicting "Low Risk" was also the highest with the sensitivity rate at 94% and an F1 score of 97%. Therefore, if a model needed to be recommended to perform this type of analysis, then this one would be the clear choice.

**Ranking of models in descending order based on "High Risk" results:**
* `EasyEnsembleClassifer`: 93.2% accuracy, 9% precision, 92% recall, and 16% F1 Score
* `BalancedRandomForestClassifer`: 78.9% accuracy, 3% precision, 70% recall and 6% F1 Score
* `SMOTE`: 65.2% accuracy, 1% precision, 61% recall and 2% F1 Score
* `SMOTEENN`: 64.5% accuracy, 1% precision, 72% recall and 2% F1 Score
* `RandomOverSampler`: 64.0% accuracy, 1% precision, 66% recall and 2% F1 Score
* `ClusterCentroids`: 54.5% accuracy, 1% precision, 69% recall and 1% F1 Score

A side note that should be considered is that original dataset had 99% of the applications classified as "Low Risk" with only 1% of the data classified in the "High Risk" category. This may skew the results greatly as there is a risk that the `Machine Learning` algorithms are creating clusters drawing from too small of a dataset of actual "High Risk" applications. This margin of risk might not be something that banks would be comfortable accepting.

# Resources

* Dataset from LendingClub: [LoanStats_2019Q1](https://github.com/amylio/Credit_Risk_Analysis/blob/main/Resources/LoanStats_2019Q1.csv)
* Software: Python 3.7.9, Anaconda 4.9.2 and Jupyter Notebooks 6.1.4
