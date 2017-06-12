
# Bandit Problem
## Describe a decision making problem in the face of uncertainty
## Setting
* a learning agent / learner
* an environment with uncertainty
* maximize total reward over time
* take an action
* gain reward (uncertain)

## Many real-world problems can be formulated as a bandit problem.
* Which version of a website drives the most revenue?
* What move should be considered next in a GO game?

## Dilemma a learner faces in the bandit problem
* Choose between options with uncertain payoffs
* Explore an option that looks inferior
* Exploit ones knowledge and go with the best-performing option
* => Exploration-exploitation dilemma


# Bandit Algorithm
## Strategy to deal with exploration-exploitation dilemma
## A mapping of `histroies` to `actions`


# Evaluation
## Regret
* Regret of a learner relative to action A
    = total reward gained when action A is kept used
    - total reward gained by a learner according to its chosen actions
* Worse-case regret = maximum regret across all actions
* A good learner achieves **sublinear** worse-case regret











