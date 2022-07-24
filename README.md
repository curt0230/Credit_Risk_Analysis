# Credit_Risk_Analysis
## Overview
The purpose of this analysis is to use multiple machine learning models to perform a credit risk analysis and identify high-risk applications.  This type of analysis can be used to greatly reduce the risk to the lender as well as significantly reducing the amount of manual work required to process applications. This problem is an example of "imbalanced machine learning" wherein the groupings (low- vs high-risk) within the sample are skewed so that most records fall in one category and very few fall into the other.  Specifically, only about 1% of our applications are likely to default.  Balanced accuracy, precision, and recall scores of all six machine learning models can be compared to evaluate the six models to determine which is most effective.

## Resources
* Software:  Python 3.9.7, Jupyter Notebooks 6.4.5
* Data source:  https://github.com/curt0230/Credit_Risk_Analysis/blob/main/LoanStats_2019Q1.csv


## Results
Six machine learning techniques were evaluated against a known set of sample data where applications were already classified as either low- or high-risk.  First, are the results of tests using linear regression models, which are preferred as the results are the most repeatable and explainable since they are derived using a linear equation.

### Linear regression
#### Oversampling
Oversampling is a technique in which samples are mocked up in the underrepresented class.  In our case, additional samples of high risk applications were generated when our machine learning model was fit on the data.  Two techniques for oversampling were tested:

##### Naive Random Oversampling
 * Balanced accuracy score: 0.63
 * Precision: 0.01
 * Recall: 0.62
 * F1 score: 0.02

Confusion Matrix
 ![confusion_matrix_oversample.png](/images/confusion_matrix_oversample.png)

Classification Report
 ![classification_report_oversample.png](/images/classification_report_oversample.png)

##### SMOTE Oversampling
 * Balanced accuracy score: 0.62
 * Precision: 0.01
 * Recall: 0.56
 * F1 score: 0.02

Confusion Matrix
 ![_confusion_matrix_oversample_smote.png](/images/_confusion_matrix_oversample_smote.png)

Classification Report
 ![classification_report_oversample_smote.png](/images/classification_report_oversample_smote.png)

Overall, based on our data set oversampling techniques yeild similar results which are prone to false positives, false negatives, and do not strike a balance between the two.  This means that many high-risk applications will slip through the cracks while many low-risk applications are flagged as being high-risk, which could lead to delayed application processing and poor customer relations if acted on incorrectly.

#### Undersampling
Undersampling is a technique in which similar samples of the overrepresented class are discarded, resulting in a much smaller set of data for training and testing the machine learning model.

 * Balanced accuracy score: 0.51
 * Precision:0.01
 * Recall: 0.56
 * F1 score: 0.01

Undersampling in this case provides similar results to the oversampling techniques and is prone to the same issues

#### Combination (Over/Undersampling)
Over and undersampling can be applied in combination as an attempt to overcome inequities in either technique.

SMOTEENN Combination Sampling:
 * Balanced Accuracy Score: 0.62
 * Precision:0.01
 * Recall: 0.68
 * F1 score: 0.02

Combination sampling in this case provides marginally better results than Naive Random Oversampling but is still prone to the same issues.

### Decision trees
Next, tree models were fitted and evaluated for performance.  These models use decision trees to classify samples and make predictions based on similar features within each sample.

Balanced Random Forest Classification:
 * Balanced Accuracy Score: 0.93
 * Precision:0.04
 * Recall: 1.00
 * F1 score: 0.07

Easy Ensemble (AdaBoost) Classification:
 * Balanced Accuracy Score: 0.93
 * Precision:0.07
 * Recall: 0.91
 * F1 score: 0.14

These models also performed similarly to eachother, but the Recall score of 100% on the Balanced Random Forest model may indicate some overfitting.  They also outperformed all the linear models in this case.  While these models are still not very precise, meaning they still flag a fairly high volume of false positives, they do identify nearly all the high-risk applications meaning they should effectively reduce risk to the lender.  However, the volume of false positives mean that all flagged applications should still be carefully reviewed by a human before any action is taken.

## Summary
Summarize the results of the machine learning models, and include a recommendation on the model to use, if any. If you do not recommend any of the models, justify your reasoning.

All machine learning models have their faults when it comes to imbalanced data sets such as this.  All models yeild relatively poor results in terms precision.  Our tree models delivered better performance in terms of recall, except the Balance Random Forest Classification technique appears to be potentially overfit. The Easy Ensemble technique using AdaBoost seems to be the best fit in this application, however due to the poor precision and imbalanced F1 scores the results should be manually reviewed prior to taking action.  This will reduce risk to the lender and also reduce the amount of manual work required for processing credit applications.