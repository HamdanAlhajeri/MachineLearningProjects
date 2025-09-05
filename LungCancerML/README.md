Sept 3rd 2025:
Started the repo and started on a lung cancer ml to predict if a patient has cancer based on their history
Finished data encoding and started basic data visualization (heat map only)
Sept 4th 2025:
Standrized the values and started the KNN model
tried the nearest neighbour for 3, 5, 7, 9 ... 21 the accuracy kept on increasing but with dimensing returns

3: 68.46
5: 69.82
7: 70.3
9: 71.06
11: 71.25
13: 71.49
15: 71.57
17: 71.49
19: 71.63
21: 71.82

13 got a 71.49% accuracy then increased to 71.57 when the neighbours to check for became 15 but decreased back to 71.49% at 17 neighbours

continue working with the model that sees 21 neighbours
confusion matrix:

|               | Predicted 0 | Predicted 1 |
|---------------|------------|------------|
| **Actual 0**  | 1002       | 2116       |
| **Actual 1**  | 702        | 6180       |
