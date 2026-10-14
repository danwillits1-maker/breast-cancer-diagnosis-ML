# **Breast Cancer Diagnosis Machine Learning Project**

## Project overview

This project explores whether measurements of cell nuclei from digitised fine-needle aspirate samples can help distinguish benign from malignant breast masses. It uses the [Wisconsin Diagnostic Breast Cancer dataset on Kaggle](https://www.kaggle.com/datasets/uciml/breast-cancer-wisconsin-data), which contains 569 samples and 30 numerical features. The target is the recorded diagnosis: benign or malignant. [UCI dataset description](https://archive.ics.uci.edu/dataset/17/breast%2Bcancer%2Bwisconsin%2Bdiagnostic)


## Aims

- Explore the diagnosis balance and how the measured features vary.
- Build a simple majority-class baseline.
- Compare the baseline with logistic regression.
- Compare and contrast different thresholds to evaluate increass in accuracy and explore varying false positive/negative results.
- Determine the strongest threshold (based of this limited model) for different real world situations.

## Testing and evaluation

Reserve a stratified 20% of the labelled data as a final holdout set. Use only the remaining training data to develop and compare models; keep the holdout untouched until the final evaluation. Fit scaling within the model pipeline to avoid using information from the holdout during training.

Report accuracy, malignant-case recall, precision, F1, ROC-AUC, and a confusion matrix. Malignant recall deserves particular attention because it shows how many malignant cases the model identifies.

## Success criteria and limitations

A successful project will produce a reproducible notebook, compare model performance against the baseline, and clearly explain how different thresholds would inform diagnosis and suggest a possible strongest threshold for this particular model. 

#### **Caveat:** This project is for learning and development not the actual creation of a tool used to assess real-world patients
