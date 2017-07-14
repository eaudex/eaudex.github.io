# ML ALGO

## KDTree
* [https://web.stanford.edu/class/cs106l/handouts/assignment-3-kdtree.pdf](https://web.stanford.edu/class/cs106l/handouts/assignment-3-kdtree.pdf)

## Naive Bayes
* [http://nlp.stanford.edu/IR-book/html/htmledition/naive-bayes-text-classification-1.html](http://nlp.stanford.edu/IR-book/html/htmledition/naive-bayes-text-classification-1.html)
* [http://nlp.stanford.edu/IR-book/html/htmledition/the-bernoulli-model-1.html](http://nlp.stanford.edu/IR-book/html/htmledition/the-bernoulli-model-1.html)


## Random Forest
### Out-of-bag Error
* Assume we build a random forest of size N
  (There are N trees in the random forest model).
* A tree is learnt on a bootstrap subset.
* For a given (xi,yi),
  lets say there are Mi bootstrap subsets containing (xi,yi),
  while there are (N-Mi) bootstrap subsets that do not contain (xi,yi).
* So there are Mi trees built upon the bootstrap subsets containing (xi,yi),
  while there are (N-Mi) tress built upon the bootstrap subsets that do not contain (xi,yi).
* We can make prediction on the given (xi,yi) using the random subforest of size (N-Mi).
* Out-of-bag error is the aggregation of the predictions over the entire training set.


* [http://stackoverflow.com/questions/18541923/what-is-out-of-bag-error-in-random-forests](http://stackoverflow.com/questions/18541923/what-is-out-of-bag-error-in-random-forests)

### Feature Selection
* Compute the out-of-bag error in the normal way
* For a given feature, scramble the feature values so that they should be no more meaningful than
  random values (although retaining the distribution of the feature values).
* [https://www.quora.com/How-do-I-find-variable-importance-in-random-forest](https://www.quora.com/How-do-I-find-variable-importance-in-random-forest)


## GBDT
* [https://statweb.stanford.edu/~jhf/ftp/trebst.pdf](https://statweb.stanford.edu/~jhf/ftp/trebst.pdf)

## Feedforward Neural Network
* [How-to-choose-the-number-of-hidden-layers-and-nodes-in-a-feedforward-neural-network](http://stats.stackexchange.com/questions/181/how-to-choose-the-number-of-hidden-layers-and-nodes-in-a-feedforward-neural-netw)
* [http://machinelearningmastery.com/neural-networks-crash-course/](http://machinelearningmastery.com/neural-networks-crash-course/)

## Linear Models
In regression,
one can model the target variable as $$y = w \cdot x$$
where $$y$$ is continuous and $$x$$ is a vector of independent variables.
In binary classification,
we do not model the target variable directly.
Instead,
we model $$z = w \cdot x$$,
where $$sgn(z)$$ indicates the class label
and $$|z|$$ indicates the confidence level.

In regression and classification,
given $$\{(x_i,y_i)\}$$
$$
\min_w \sum loss(w, x_i, y_i)
$$


# Ranking
* Pointwise
    * model label-instance point
    * (real-valued / ordinal) regression
* Pairwise
    * model the pairwise ranking
    * minimize pairwise loss
* Listwise
    * model the entire ranking
    * ??

## RankSVM
Given a set of instance-relevance-query tuples $$(x_i,y_i,q_i)$$
where $$x_i \in R^d$$ is the data point, $$y_i \in R$$ is the relevance score,
and $$q_i \in Z$$ is the query.

RankSVM solves the following optimization problems
$$
\min_w \sum_{(i,j) \in P} \max(0, 1-w \cdot (x_i-x_j))
$$
where the set of preference pairs
$$
P \equiv \{(i,j) \mid y_i > y_j, q_i = q_j \}
$$


