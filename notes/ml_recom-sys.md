# Recommender System

* [https://en.wikipedia.org/wiki/Collaborative_filtering](https://en.wikipedia.org/wiki/Collaborative_filtering)
* [http://alex.smola.org/teaching/berkeley2012/slides/8_Recommender.pdf](http://alex.smola.org/teaching/berkeley2012/slides/8_Recommender.pdf)

## ALGO
### Neighborhood-based

#### User-based
* Input:
    1. the user-item interaction, R

#### Item-based
* Input:
    1. the user-item interaction, R

---

### Content-based
1. Input:
    1. the user profiles, U
    2. the user-item interaction, R

2. Input:
    1. the item profiles, I
    2. the user-item interaction, R

---

### Model-based

#### Matrix factorization
* Input:
    1. the user-item interaction, R

* Matrix factorization
    1. Real-valued MF
    2. Binary MF
    3. One-class MF

#### Inductive matrix factorization
* Input:
    1. the user profiles, U
    2. the item profiles, I
    3. the user-item interaction, R

---

### Hybrid
* Input:
    1. the user profiles, $$U$$
    2. the item profiles, $$I$$
    3. the user-item interaction, $$R$$

* Step 1: Use the neighborhood-based / model-based approaches on $$R$$.
* Step 2: Find the top $$k$$ items for each user.
* Step 3: Collect (label, features) for a live event, (user, item, timestamp).
    * label:
        * e.g. click or not
        * e.g. convert or not
    * features:
        * user features
            * profile: demographics
            * behavior: action taken in a
        * item features
            * profile
            * behavior
        * user-item interaction features








