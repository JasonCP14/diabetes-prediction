# Diabetes Detection

In this project, we used 3 fine-tuned classification models: Logistic Regression,  to detect diabetes based on multiple patient features. This report will give a brief comparison of the three models.

**Disclaimer: Analysis that leads to the choice of data preprocessing and handling methods can be seen in detail inside the notebook**


## 1. Evaluation Metrics

First of all, we will show the evaluation metrics of the 3 models here.

**1) Logistic Regression**

a) Imbalanced Data
|                     | Predicted Negative | Predicted Positive |
|---------------------|--------------------|--------------------|
| **Actual Negative** | 1525               | 12                 |
| **Actual Positive** | 152                | 10                 |

| Accuracy  | Precision | Recall    | F1 Score  |
|-----------|-----------|-----------|-----------|
| 0.90      | 0.45      | 0.06      | 0.11      |

b) SMOTE Data
|                     | Predicted Negative | Predicted Positive |
|---------------------|--------------------|--------------------|
| **Actual Negative** | 1167               | 370                |
| **Actual Positive** | 23                 | 139                |

| Accuracy  | Precision | Recall    | F1 Score  |
|-----------|-----------|-----------|-----------|
| 0.77      | 0.27      | 0.86      | 0.41      |

**2) Decision Trees**

a) Imbalanced Data
|                     | Predicted Negative | Predicted Positive |
|---------------------|--------------------|--------------------|
| **Actual Negative** | 1485               | 52                 |
| **Actual Positive** | 57                 | 105                |

| Accuracy  | Precision | Recall    | F1 Score  |
|-----------|-----------|-----------|-----------|
| 0.94      | 0.67      | 0.65      | 0.66      |

b) SMOTE Data
|                     | Predicted Negative | Predicted Positive |
|---------------------|--------------------|--------------------|
| **Actual Negative** | 1316               | 221                |
| **Actual Positive** | 45                 | 117                |

| Accuracy  | Precision | Recall    | F1 Score  |
|-----------|-----------|-----------|-----------|
| 0.84      | 0.35      | 0.72      | 0.47      |

**3) Random Forest**

a) Imbalanced Data
|                     | Predicted Negative | Predicted Positive |
|---------------------|--------------------|--------------------|
| **Actual Negative** | 1489               | 48                 |
| **Actual Positive** | 65                 | 97                 |

| Accuracy  | Precision | Recall    | F1 Score  |
|-----------|-----------|-----------|-----------|
| 0.93      | 0.67      | 0.60      | 0.63      |

b) SMOTE Data
|                     | Predicted Negative | Predicted Positive |
|---------------------|--------------------|--------------------|
| **Actual Negative** | 1439               | 98                 |
| **Actual Positive** | 52                 | 110                |

| Accuracy  | Precision | Recall    | F1 Score  |
|-----------|-----------|-----------|-----------|
| 0.91      | 0.53      | 0.68      | 0.59      |


## 2. Imbalanced vs SMOTE

First of all, we will compare the imbalanced models and SMOTE models in general. There are a few things to be observed:
- Imbalanced models tend to have a significantly higher accuracy and precision
- SMOTE models meanwhile tend to have a higher recall 

On paper, imbalanced models may look better due to a vast difference in accuracy. However, this comes at a cost of precision, recall, and F1-score. As we know, type 1 errors in the healthcare world is very undesirable, as it is better to falsely detect a disease, rather than failing to detect one (recall is important). And as we can see in the confusion matrices above, the imbalanced models tend to predict 0 (negative) during the testing due to its training nature. 

For example, in the logistic regression model above, the accuracy dropped by 0.13 when switching to SMOTE data due to the higher number of false positive prediction. That however, was traded off with a 13x higher true positive count and a 0.8 increase in recall. This effect can still be seen, but is not as drastic in the other 2 models.


## 3. Model Comparison

Now that, we have decided that SMOTE is better in our scenario, we should decide which of the 3 models is the best, and there are a few ways to determine this.

First of all, is by simply looking at the accuracy and overall metrics, which clearly points to random forest. It is slightly better than decision trees, and miles better than the logistic regression. 

A more unorthodox way of looking at the results is by looking at the recall alone. This is most of the times undesirable, as we can rack up the metric by predicting positives most of the time, and thus is easily manipulatable. Nevertheless, this provides another point of view should the disease is really dangerous. In this case, logistic regression is the winner.


## 4. Future Researches

As this is a short-term research, there are still gaps to fill. One of them is that SMOTE might not be the best sampling solution to be used, as there are other methods that may be better in this problem. For example, undersampling, mixture of oversampling-undersampling, etc.






