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


## Research Question

Does immediate repetition of a word increase the probability of answering correctly?

## Methodology

1. Parsed raw SLAM sequential learner interaction data.
2. Constructed a treatment variable:
   - `treatment = 1` if the same word appeared in the immediately previous interaction.
3. Constructed a lag variable:
   - `prev_correct` for user-word memory state.
4. Controlled for temporal dependencies.
5. Addressed class imbalance via undersampling.
6. Estimated treatment effect using logistic regression.

## Key Findings

- Raw analysis shows higher correctness under repetition.
- After controlling for previous correctness:
  - Treatment coefficient is positive.
  - Odds ratio > 1, suggesting repetition increases probability of correctness.
- Demonstrates importance of modelling adaptive assignment in educational systems.

## Relevance

This project demonstrates:
- Longitudinal data processing
- Treatment construction from logs
- Causal reasoning in adaptive systems
- Handling imbalanced educational data

## How to Run

```bash
pip install -r requirements.txt
python duolingo_causal_pipeline.py

# Conclusion

This project demonstrates how large-scale educational data can be used for causal analysis in learning environments.

While immediate repetition appears negatively associated with correctness, the result highlights the importance of careful causal identification in adaptive systems.
