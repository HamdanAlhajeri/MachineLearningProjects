Sept 3rd 2025:
Started the repo and started on a lung cancer ml to predict if a patient has cancer based on their history
Finished data encoding and started basic data visualization (heat map only)
Sept 4th 2025:
Standrized the values and started the KNN model
tried the nearest neighbour for 3, 5, 7, 9 ... 21 the accuracy kept on increasing but with dimensing returns

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
confusion matrix:

|               | Predicted 0 | Predicted 1 |
|---------------|------------|------------|
| **Actual 0**  | 1002       | 2116       |
| **Actual 1**  | 702        | 6180       |


| Class            | Precision | Recall | F1-score | Support |
| ---------------- | --------- | ------ | -------- | ------- |
| 0.0              | 0.59      | 0.32   | 0.42     | 3118    |
| 1.0              | 0.74      | 0.90   | 0.81     | 6882    |
| **Macro avg**    | 0.67      | 0.61   | 0.61     | 10000   |
| **Weighted avg** | 0.70      | 0.72   | 0.69     | 10000   |


| Metric  | Value |
| ------- | ----- |
| ROC-AUC | 0.722 |
