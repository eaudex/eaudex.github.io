# ML Modeling

Given a problem statement

## Understand the problem we are trying to solve
* **Ask questions**
* What is the scenario?
    * Entities:
        * Who / what get involved in the scenario?
          e.g. ads, users, products, keywords, movies, ...
    * How do entities interact with each other?
* What is the goal?
    * #views
    * #clicks
    * #conversions
    * ...

## Data Understanding
* What data do we have?
* Data schema
    * What does each row mean?
    * What does each column mean?
* Data size
    * #rows
    * #columns
    * #entities

## Feature Extraction / Feature Engineering
* An entite:
    * static features: e.g. text
    * behavioral features: e.g. traffic
        * time-dependent
        * location-dependent
* An interaction between entities:
    * static features:
    * behavioral features
        * time-dependent
        * location-dependent

## Modeling
* **All About Prediction**
    * classification
    * regression
    * ranking

* Example 1: click through rate prediction

* Example 2: recommendation system
    * ranking problem
    * collaborative filtering
    * matrix factorization


## Algorithms
* Classification
    * logistic regression
    * support vector machine
    * ---
    * decision tree
    * random forest
    * gradient-boosted decision tree
    * ---
    * bagging
    * boosting

* Regression
    * linear regression
    * support vector regression
    * ---
    * decision tree
    * random forest
    * gradient-boosted decision tree
    * ---
    * bagging
    * boosting

* Ranking
    * point-wise approach
        * classification
        * regression
    * pair-wise approach
        * ranked support vector machine
        * bayesian personalized ranking
    * list-wise approach
        * ???


## Validation
* train / test split
* in case of time-dependent scenario, split should be based on timestamp
* train / validation split
* cross validation




## Challenges
* users behaviors are so dynamic
* many machine learning algorithms are developed based on the assumption
  that data follows a stationary probability distribution





## Formulation

* Data: ${(x,y)}$
* Model: $s \approx f(x)$
    * regression: $s =  \hat{y}$
    * binary classification: $\hat{y} = I(s >= t)$ where $t$ is a pre-defined threshold
* Loss: to evaluate how well the model performs
    * squared loss
    * logistic loss
    * hinge loss
    * squared hinge loss
* Learning / Training:
    * Minimize the loss caused by the discrepency between predicted and desired output
    * This is where the optimization algorithm comes in
        * gradient descent
        * coordinate descent
        * ...
* Evaluation:
    * Metric: have to tied to high-level objective (e.g. business goal)
        * mean squared error
        * accuracy
        * area under ROC curve
        * area under PR curve
        * ...
    * Why not use loss itself to evaluate?
        * Ans: the loss is not intuitive enough in terms of high-level objective
    * Why not turn high-level objective into loss and then optimize it?
        * Ans: resulting loss might not be easy to be optimized
            * Not smooth, e.g. 0/1 loss
* Validation:
    * training / testing data split
    * try different models and their hyper-parameters
    * validate model performance on the testing data split in terms of the pre-defined metric


## Overfitting
### Detect Overfitting

### Prevent Overfitting

#### More Data

#### Early Stopping
* It can be interpreted as regularization in time
* An optimizatino algorithm e.g. gradient descent tends to learn a
  more and more complex model as the number of iterations increases.

#### Regularization (Adding a Regularization Term)
* Add $$\lambda \|w\|_2$$ or $$\lambda \|w\|_1$$ to the original loss function

* Why it works?
    * A simple model can perform well on the observed data; then it is always preferred.
    * By learning theory, the generalization *error bound* increases
      as the size of the model search space (hypothesis set) increases.
    * => A regularization term is to limit model search space in terms of **model complexity**
        * By changing the value of $$\lambda$$ to select a model starting from
          a *small* search space only including *simple* models
    * In summary,
        1. Simple models first
        2. Small model space (hypothesis set) first
        * $$\lambda$$: from large to small

* Regularization can prevent overfitting
    * Regularization provides a way to control model complexity by changing the value of $$\lambda$$.
    * Minimizing the ~~training error~~ is NOT enough; what we want is beyond that...
    * We want our model to generalize well to unseen data.
    * That is, we care about the ~~generalization error~~.
    * Minimizing the ~~generalization error~~ is the goal.
    * Generalization error <= training error + model complexity ?? (double check)

* $$\|w\|$$ to measure model complexity
    * A simple model has smaller weights... Why??




