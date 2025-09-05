Sept 3rd 2025:
Started the repo and started on a lung cancer ml to predict if a patient has cancer based on their history
Finished data encoding and started basic data visualization (heat map only)
Sept 4th 2025:
Standrized the values and started the KNN model

Sept 5th 2025:
tried the nearest neighbour for 3, 5, 7, 9 ... 21 the accuracy kept on increasing but with dimensing returns

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

|               | Predicted 0 | Predicted 1 |
|---------------|------------|------------|
| **Actual 0**  | 1002       | 2116       |
| **Actual 1**  | 702        | 6180       |

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


### ROC-AUC

| Metric  | Value |
| ------- | ----- |
| ROC-AUC | 0.722 |

what is ROC-AUC?
it measures the model’s ability to distinguish between classes
0.5 would mean that it's just randomly guessing and 1.0 would mean has perfect discrimination
in our case we got 0.722 which is a decent seperation but not accurate and has a lot of room for improvment