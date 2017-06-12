# Feature Selection

## Any Model
* Run cross validation on the original data set
* Compute the cross validation accuracy $$ACC_0$$
* For a given feature
    * Remove the feature from the original data set
    * Run cross validation on the resulting data set $$ACC_i$$
    * Compare the cross-validation accuracy, $$\Delta_i = |ACC_i-ACC_0|$$

## Linear Model
* $$|w_i|$$

## L1 Regularization + Linear Model
* Push weights to zeros

## Random Forest
* Build a random forest on the original data set
* Compute the out-of-bag error $$Err_0$$
* For a given feature
    * Scramble the feature values in the original data set
    * Build a random forest on the resulting data set
    * Compute the out-of-bag error $$Err_i$$
    * Compare the out-of-bag error, $$\Delta_i = |Err_i - Err_0|$$

* [http://stackoverflow.com/questions/18541923/what-is-out-of-bag-error-in-random-forests](http://stackoverflow.com/questions/18541923/what-is-out-of-bag-error-in-random-forests)
* [https://www.quora.com/How-do-I-find-variable-importance-in-random-forest](https://www.quora.com/How-do-I-find-variable-importance-in-random-forest)

