# Google - AutoML Modeling Report

[![License: MIT](https://img.shields.io/badge/License-MIT-brightgreen.svg)](https://opensource.org/licenses/MIT)

## TODO - OVERVIEW...

### Binary Classifier with Clean/Balanced Data

**Train/Test Split**

How much data was used for training? How much data was used for testing?

* 200 images (100 for each label: pneumonia and normal) were used for training.
* 14 images of each label were used for testing. 

![Clean Balanced Training](images/clean-balanced-training.png)

**Confusion Matrix**

What do each of the cells in the confusion matrix describe? What values did you observe (include a screenshot)? What is the true positive rate for the “pneumonia” class? What is the false positive rate for the “normal” class?

The Confusion Matrix grid shows all the predicted labels relative to all the true labels (or, what is the same, each cell shows the relation between the true label and the predicted label).

The values across a row should add up to 100%. Values in the columns have no limitations. 

![Confusion Matrix](images/confusion-matrix.png)
*Image credits*: https://twitter.com/narkhede_sarang

The cells show:
1. TP: True Positive. Example: we predicted pneumonia and it is pneumonia.
2. FP: False Positive. Example: we predicted pneumonia and its is normal. 
3. FN: False Negative. Example: we predicted that is NOT pneumonia and it IS pneumonia.
4. TN: True Negative. Example: we predicted that is NOT pneumonia and it is NOT pneumonia.

The result was…
* 100% of the true cases of the label “normal” were classified as “normal” 100% of the times
* 100% of the true cases of the label “pneumonia” were classified as “pneumonia” 100% of the times.

The true positive rate for the “pneumonia” class was 100%.
The false positive rate for the “normal” class was 0%.

![Clean Balanced Confusion Matrix](images/clean-balanced-cm.png)

**Precision & Recall**

What does precision measure?
What does recall measure? What precision and recall did the model achieve (report the values for a score threshold of 0.5)?

Precision measures the percentage of correct predictions against total number of predictions.  
Formula: TP / (TP + FP)

Recall measures the percentage of correctly identified instances of total possible instances.
Formula: TP / (TP + FN)

Or, from Google’s Docs… “Precision and recall help us understand how well our model is capturing information, and how much it’s leaving out. Precision tells us, from all the test examples that were assigned a label, how many actually were supposed to be categorized with that label. Recall tells us, from all the test examples that should have had the label assigned, how many were actually assigned the label”

* Score threshold: 0.50
* Recall: 1.000
* Precision: 1.000

![Clean Balanced Precision and Recall](images/clean-balanced-pr.png)

**Score Threshold**

When you increase the score threshold, what happens to precision? 
What happens to recall? Why?

If we increase the threshold our model will classify fewer images, but it will have a lower risk of misclassifying these assets (model will have more confidence)
In consequence…
* Precision will increase
* Recall will decrease 

Side note: if we decrease the threshold, our model will; classify more images but with less precision (risk of misclassifying assets)

### Binary Classifier with Clean/Unbalanced Data

**Train/Test Split**

How much data was used for training? How much data was used for testing?

* 400 images (100 for normal and 300 for pneumonia) were used for training.
* 45 images of each label were used for testing. 

![Clean unbalanced training](images/clean-unbalanced-training.png)

**Confusion Matrix**

How has the confusion matrix been affected by the unbalanced data? Include a screenshot of the new confusion matrix.

In our evaluation 10.8% of true cases of pneumonia were classified as normal.

*IMPORTANT:*

This is a strange output. 
I would expect to have more images classified as pneumonia since we are “biasing” the model using 3 times (300) the quantity of assets for pneumonia in relation to normal (100).
I talked with my mentor and she told me to re build the model, however, I’m still receiving a result similar to the previous one. 

However, to answer the rubric’s question… In unbalanced/clean, model will bias towards the label or class with more images. In this case, pneumonia. Or what is the same, in the Confusion Matrix we could see cases of normal flagged as pneumonia since our model will classify more cases as pneumonia and less as normal.

![Clean unbalanced Confusion Matrix](images/clean-unbalanced-cm.png)

**Precision & Recall**

How have the model’s precision and recall been affected by the unbalanced data? (Report the values for a score threshold of 0.5.)

* Precision: 91.1%
* Recall: 91.1%

![Clean unbalanced Precision and Recall](images/clean-unbalanced-t.png)

Compared with the clean/balanced data, both, precision and recall decreased.

**Unbalanced classes**

From what you’ve observed, how do unbalanced classes affect a machine learning model?

It generates bias making the model tend to the “most common” label (aka, misclassification).

### Binary Classifier with Dirty/Balanced Data