
# Handling Unbalanced Labeled Data
* 0: majority label
* 1: minority label

## Down-sampling

## Over-sampling

## Panelizing under-represented data

## AUC: area under ROC (TPR vs FPR)
* probability that a classifier ranks a randomly chosen positive data point
  above a randomly chosen netative data point.
* When a threshold changes from high to low, #TP data points and #FP points increase.
  In case where the increasing rate of #TPs is about the same as the increasing
  rate of #FPs, the classifier does random guessing
* It is insensitive to imbalanced classes
* It only cares about ranking, but does not care about predicted values


