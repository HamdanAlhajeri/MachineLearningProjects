Sept 3rd 2025:

Started the repo and started on a lung cancer ml to predict if a patient has cancer based on their history
Finished data encoding and started basic data visualization (heat map only)

Sept 4th 2025:
Standrized the values and started the KNN model

----------------------------------------------------
Tried the nearest neighbour for 3, 5, 7, 9 ... 21 the accuracy kept on increasing but with dimensing returns

# KNN Results  

3: 68.46%  
5: 69.82%  
7: 70.3%  
9: 71.06%  
11: 71.25%  
13: 71.49%  
15: 71.57%  
17: 71.49%  
19: 71.63%  
21: 71.82%  

13 got a 71.49% accuracy then increased to 71.57 when the neighbours to check for became 15 but decreased back to 71.49% at 17 neighbours

continue working with the model that sees 21 neighbours
## Confusion matrix:

|              | Predicted 0 (No Cancer) | Predicted 1 (Cancer) |
| ------------ | ----------------------- | -------------------- |
| **Actual 0** | 1002                    | 2116                 |
| **Actual 1** | 702                     | 6180                 |


TN A0P0 is the model correctly predicting that patients don't have cancer       
FP A0P1 is the model incorrectly predicting that patients have cancer  
FN A1P0 is the model incorrectly predicting that patients don't have cancer  
TP A1P1 is the model correctly predicting that patients have cancer  

## Classification Report

| Class            | Precision | Recall | F1-score | Support |
| ---------------- | --------- | ------ | -------- | ------- |
| 0.0              | 0.59      | 0.32   | 0.42     | 3118    |
| 1.0              | 0.74      | 0.90   | 0.81     | 6882    |
| **Macro avg**    | 0.67      | 0.61   | 0.61     | 10000   |
| **Weighted avg** | 0.70      | 0.72   | 0.69     | 10000   |

### Classes 

Class 0 (no cancer):  
Precision 0.59 of all patients that the model predicted as 0 (no cancer) 59% where actually 0  
Recall 0.32 of all the actually 0 patients the model only correctly identified 32%  
F1-score 0.42 the harmonic mean between precision and recall -> F1 = 2 * (Precision * Recall) / (Precision + Recall)  
Support 3118 actually class 0  

Class 1 (cancer):  
Precision 0.74 of all patients that the model predicted as 1 (cancer) 74% where actually 1   
Recall 0.90 of all the actually 1 patients the model only correctly identified 90%  
F1-score 0.81 the harmonic mean between precision and recall -> F1 = 2 * (Precision * Recall) / (Precision + Recall)  
Support 6882 actually class 1


## ROC-AUC

| Metric  | Value |
| ------- | ----- |
| ROC-AUC | 0.722 |

what is ROC-AUC?  
it measures the model’s ability to distinguish between classes  
0.5 would mean that it's just randomly guessing and 1.0 would mean has perfect discrimination  
in our case we got 0.722 which is a decent seperation but not accurate and has a lot of room for improvment  


### Changing threshold

First let's try to understand what a threshold in a KNN, in sklearn the base threshold is 0.5 that mean's that the target class (in our case here that the patient has lung cancer) we need at least half of the neighbours to be cancer for the input to return cancer but if we change the threshold to 0.3 we only need a third of the surrounding classes to be cancer, this basically means that the model is more sensetive. In theory it should allow the model to more likely to predict that a patient actually has cancer.  
Since as mentioned previously by defualt the threshold for a KNN in sklearn is 0.5 let's try changing the threshold to 0.3 and we got the following results

## Confusion matrix

|              | Predicted 0 (No Cancer) | Predicted 1 (Cancer) |
| ------------ | ----------------------- | -------------------- |
| **Actual 0** | 245                     | 2873                 |
| **Actual 1** | 84                      | 6798                 |

We got better results now that we decreased the threshold now there is more patients that actually have cancer that got predicted where before out of 10,000 patients we had 702 patients where predicted to be healthy when they actually they have cancer but now the number has decreased to 84. But the number of healthy patients that where predicted to have cancer went from 2116 to 2873 which is a significant jump.

## Classification report

| Class            | Precision | Recall | F1-score | Support |
| ---------------- | --------- | ------ | -------- | ------- |
| 0.0              | 0.74      | 0.08   | 0.14     | 3118    |
| 1.0              | 0.70      | 0.99   | 0.82     | 6882    |
| **Macro avg**    | 0.72      | 0.53   | 0.48     | 10000   |
| **Weighted avg** | 0.72      | 0.70   | 0.61     | 10000   |

This further supports what was stated in the confusion matrix 99% (0.99 from recall) of the cancer patients where predicted correctly but for the actually healthy patients only 8% where predicted correctly which means it has a high error for False Positives

## ROC-AUC

| Metric  | Value |
| ------- | ----- |
| ROC-AUC | 0.722 |


## KNN measurments

This time I tried changing how the KNN would check the surrounding neighbors by changing:  
I tried every combination of neighbors tried previously (3 to 21 odds) with manhattan and minkowski for distance, uniform and distance for weights this yeilds a total of 40 diffrent combinations and the best combination found was 21, manhattan and uniform but this result was worse than the previous which was 21 euclidian. 

## Solution

I'd like to try another meathod this time, we will use the heat map previously aquired in order to pick the 3 features that are most correlating with lung cancer  
Even after picking only the 3 features that are most correlating there isn't much improvment.

### What's next?

Since the base KNN 21 neighbors model was the best out of all KNN models we'll finalize that and attempt another meathod, I'd like to attempt using something like a tree I have 3 options Decision Tree, Random Forest Tree and Gradient Boosting, as of writing thins I don't understand Random Forest tree or Gradient Boosting but I'd like to attempt to understand them before I pick a model.

I decided I will go with a random forest tree as it isn't as prone to overfitting as a decision tree and it will take into considration many decision tree's output (in our case here 200 trees)

The random forest tree ended up giving worse results than the KNN (somehow?) so let's try another meathod

It's a bit of a bigger jump but I'd like to try and build a Neural Network and see what happens


Test commit