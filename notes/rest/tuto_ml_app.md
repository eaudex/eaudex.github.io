# ML APP

## How much data is enough?
* $$l$$ and $$n$$ denode the number of examples and features, respectively.
* Normally, $$l$$ should be at least greater than $$n$$.
* As a rule of thumb, $$l$$ should be 10 times as many as $$n$$.
* In some use cases such as document classification, data is wide and sparse.
  Even though we may not have enough examples, obtaining a good model is still
  possible through regularization/prior.
* Afterall, how much data is enough only can be known through validation.
* [http://fastml.com/how-much-data-is-enough/](http://fastml.com/how-much-data-is-enough/)
* [https://www.csie.ntu.edu.tw/~cjlin/libsvmtools/#how_large_the_training_set_should_be?](https://www.csie.ntu.edu.tw/~cjlin/libsvmtools/#how_large_the_training_set_should_be?)
* [https://medium.com/@malay.haldar/how-much-training-data-do-you-need-da8ec091e956#.piinvfov4](https://medium.com/@malay.haldar/how-much-training-data-do-you-need-da8ec091e956#.piinvfov4)


## Is feature selection necessary?
* [http://stats.stackexchange.com/questions/149446/do-we-still-need-to-do-feature-selection-while-using-regularization-algorithms](http://stats.stackexchange.com/questions/149446/do-we-still-need-to-do-feature-selection-while-using-regularization-algorithms)

* The more choices one makes to build a model,
the more data we need to make the model stable.
Feature selection usually introduces another layer of complexity,
and may likely to cause poor generalization performance
if the validation schema is not designed properly.

* Use Case 1: Given a fixed learner e.g. LR.
We just have a few data points, 100 for example,
but a data point has millions of features.
Feature selection can help avoid over-fitting.
A linear model with millions of variables has too much representation power.
It is likely to overfit such a data set with 100 data points.


## What would we do overfitting/underfitting?
* When the training error looks small but the test error is not as small,
  overfitting is happening.
* When the training error looks high and the test error is also high,
  underfitting is happening.

|         |       | Test    | Error |
| ---     | ---   | ------- | ----- |
|         |       | Low     | High  |
| Train   | Low   | Perfect | Overfitting  |
| Error   | High  | No Way  | Underfitting |



## Customer Behavior Prediction
* [https://www.altocloud.com/blog/how-machine-learning-can-be-used-to-predict-customer-behaviour](https://www.altocloud.com/blog/how-machine-learning-can-be-used-to-predict-customer-behaviour)
* [http://www.strong.io/blog/predicting-customer-behavior-machine-learning-to-identify-paying-customers](http://www.strong.io/blog/predicting-customer-behavior-machine-learning-to-identify-paying-customers)
* [https://www.linkedin.com/pulse/how-machine-learning-can-used-predict-customer-behaviour-aherne](https://www.linkedin.com/pulse/how-machine-learning-can-used-predict-customer-behaviour-aherne)



## CTR Prediction for Online Advertising
* KDDCup-2012: [https://github.com/myui/hivemall/wiki/KDDCup-2012-track-2-CTR-prediction-dataset#converting-feature-representation-by-feature-hashing](https://github.com/myui/hivemall/wiki/KDDCup-2012-track-2-CTR-prediction-dataset#converting-feature-representation-by-feature-hashing)

