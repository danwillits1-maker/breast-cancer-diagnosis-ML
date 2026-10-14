# Breast cancer classification and the cost of different decisions

## Project aim

With an understanding of the NHS, I wanted to explore what a model's performance would mean for patients and the staff reviewing its predictions.

This project uses breast-mass data to compare decision thresholds. The question is straightforward: how many more malignant cases does a lower threshold catch, and how many extra false alarms does it create?

The NHS provides a hypothetical setting for discussing these decisions. This is a learning project, with no clinical deployment or measured cost savings.

## Data and methods

The dataset contains 569 samples and 30 measurements describing cell nuclei. These measurements come from samples already collected through fine needle aspiration, so a possible application would support assessment after sampling. [Dataset documentation](https://archive.ics.uci.edu/dataset/17/breast-cancer-wisconsin-data-set)

I prepared the data and used a stratified split of 60% for training, 20% for validation and 20% for testing. I compared a majority-class baseline with logistic regression, using a pipeline to standardise the inputs.

I trained logistic regression once, then applied five thresholds to its probability estimates. The validation results informed the threshold choice.

## Results

| Threshold | Accuracy | Malignant recall | False positive rate | False negative rate | False positives | False negatives |
|---:|---:|---:|---:|---:|---:|---:|
| 0.50 | 97.4% | 97.7% | 2.8% | 2.3% | 2 | 1 |
| 0.40 | 97.4% | 97.7% | 2.8% | 2.3% | 2 | 1 |
| 0.30 | 95.6% | 97.7% | 5.6% | 2.3% | 4 | 1 |
| 0.20 | 92.1% | 97.7% | 11.3% | 2.3% | 8 | 1 |
| 0.10 | 88.6% | 100.0% | 18.3% | 0.0% | 13 | 0 |

Thresholds of 0.40 and 0.50 produced identical validation predictions. I took 0.40 forward for test evaluation.

Lowering the threshold to 0.30 or 0.20 added false positives without catching the remaining malignant case. At 0.10, the model caught every malignant validation case, but flagged 13 benign samples.

An exploratory comparison on test data showed a different outcome. At 0.10, accuracy fell without an improvement in malignant recall compared with 0.40.

## What this could mean for a healthcare service

On validation, moving from 0.40 to 0.10 caught one additional malignant case and generated 11 additional false positives.

If every positive prediction prompted a review, the number of flagged samples would rise from 44 to 56. Those flags would not necessarily lead to another appointment or biopsy; the consequences would depend on the clinical workflow.

Avoiding missed malignancies matters, but additional reviews also take staff time and can cause patient concern. Accuracy alone cannot tell a service which threshold offers the best use of its resources. That decision would need evidence about patient outcomes, review capacity and the costs of both types of error.

## Limitations

This small dataset does not establish performance in an NHS population. Catching every malignant validation case does not guarantee the same result on new data.

Earlier experiments also compared thresholds on test data, so the results remain exploratory. I have not assessed probability calibration or measured clinical outcomes, workload or costs.

## Conclusion

Lowering the threshold helped detect more malignant cases in validation, but that benefit did not repeat in the test comparison. It also increased false alarms.

The experiment shows why a healthcare service needs to understand the errors behind an accuracy score before deciding how to use a model.
