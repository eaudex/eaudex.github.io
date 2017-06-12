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















