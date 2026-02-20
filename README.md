# Causal-modelling-Causal-Effect-of-Immediate-Repetition-on-Second-Language-Learning
This study uses the Duolingo SLAM 2018 dataset, released for the Shared Task on Second Language Acquisition Modeling. 
Causal Modeling of Second Language Learning
Duolingo SLAM 2018 Dataset

This project explores the causal effect of immediate word repetition on learner accuracy in second language acquisition, using large-scale educational data from Duolingo.

# 1. Dataset

This study uses the Duolingo SLAM 2018 dataset, released for the Second Language Acquisition Modeling shared task.

# 2. Key properties:

~2 million word-level learner responses

~6,000 learners

First 30 days of learning activity

Spanish learners learning English (es_en track)

Each row represents a learner’s attempt at producing or recognizing a single word.

# 3. Variables
Original Variables

user_id – learner identifier

instance_id – unique token attempt ID

token – word being practiced

pos – part-of-speech tag

dep_rel – syntactic dependency relation

correct – binary outcome (1 = correct, 0 = incorrect)

# 4. Engineered Variables

exercise_id – derived from instance_id

treatment – indicator for immediate repetition

word_accuracy – average correctness rate per word (proxy for word difficulty)

# Research Question

Does immediate repetition of a word increase the probability of a correct response?

This question is motivated by theories of spacing, memory consolidation, and adaptive learning.

# Treatment Definition

A word is considered treated (treatment = 1) if the learner encountered the same word in the immediately preceding exercise.

Otherwise:

treatment = 0

This approximates a short-term repetition intervention.

# Methodology

A logistic regression model was used to estimate the relationship between repetition and correctness.

# Outcome:

correct

Covariates:

# treatment

pos

dep_rel

word_accuracy

Categorical variables were one-hot encoded.
The treatment coefficient is interpreted as an estimate of the causal effect under standard assumptions.

# Results
Raw Accuracy by Treatment Group
Treatment	Mean Accuracy
No repetition (0)	14.39%
Immediate repetition (1)	8.13%
Logistic Regression Estimates

Treatment coefficient: −0.343

Odds ratio: 0.71

Interpretation:
Immediate repetition is associated with approximately 29% lower odds of correctness.

# Interpretation

The negative effect likely reflects confounding rather than harm:

Difficult words are more likely to be repeated

Difficult words also have lower accuracy

Repetition is adaptively assigned, not randomized

Thus, repetition serves as a signal of difficulty.

# Limitations

Treatment assignment is endogenous

No learner fixed effects

Limited control for temporal dynamics

Future work could apply:

Fixed-effects models

Causal forests

Doubly robust estimators

Dynamic treatment effect modeling

# Conclusion

This project demonstrates how large-scale educational data can be used for causal analysis in learning environments.

While immediate repetition appears negatively associated with correctness, the result highlights the importance of careful causal identification in adaptive systems.
