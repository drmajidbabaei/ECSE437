---
layout:
  title:
    visible: true
  description:
    visible: false
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
---

# Topic#9 \[Taken]

Topic 9: [Learning-to-rank vs ranking-to-learn: Strategies for regression testing in continuous integration](https://dl.acm.org/doi/abs/10.1145/3377811.3380369?casa\_token=589-48O3V2YAAAAA:ZHmEK7dF7uSAaucGLiSxQJPDa\_EmDpmSByQIRa\_itN02J3YsacGJ26cHo6Ns2AEuQREYlw3A7Q57)

{% hint style="warning" %}
This topic is taken by **Biruk berhanu Retta**
{% endhint %}


## Introduction

The paper aims to compare different machine learning algorithms in respect to their effectiveness during selection and filtering of test suites. It also takes into account different experimental factors such as variability of code and time between commits.

## Background information on regression testing

Regression Testing makes sure there are no rollbacks in quality. It uses a pre-existing set of tests to acheive this.Testing is time constrained problem dealt with by proper selection and prioritization.
During selection the goal is to select only those tests exercising the code directly or indirectly affected by changes. Prioritization reorders the entire test suite so that tests with higher priority are run first. They can be combined, by selecting a subset of tests, then prioritizing them, or by prioritizing the suite, then selecting tests.

## ML for selection and  prioritization

Learning to Rank is a supervised learning where the algorithm is trained on a labeled dataset. Training is done on a number of observations, depending on the amount of history available; the resulting model is used to prioritize tests for next commits. The model needs to be re-trained from time to time: this is preferred to online learning when training is expensive (e.g., for a large codebase).

Ranking to Learn is reinforcement learning where the agent learns by receiving feedback in the form of rewards or punishments as it interacts with its environment. Training is done online, namely when the agent updates its knowledge about state-action-reward. RTL algorithms take much longer, since training is repeated at each commit. But RTL can rank test cases since the beginning.

## Experimental factors

It investigates what factors make some ML algorithms behave better than others for test prioritization in a CI context. It focuses on characteristics of the code under test and of the CI process.
The code under test factors include 

    * The variability of the code/test metrics;
    
    * The failure proneness of the code, which causes more or less balanced datasets;
    
    * The code/test metrics that can be used as features for training and improving prediction.
The CI process factors include

    * The inter-commit time, which determines the time available for performing TS&P;
    
    * The cycle size (i.e., size of the sample, or number of tests, per commit), which affects the length of the history available for learning.

## Results
### RPA is the metric used to measure accuracy
MART and L-MART have the best RPA and medium-level ranking and training times. 
CA performs poorer but is better for ranking time with a medium-level training time. 
KNN requires less training time than others LTR, but it takes long for ranking, not justifiably paid off by the RPA. 
RL algorithms require high training times, being online learning schemes. 
RL-RF has high ranking times, but good RPA. RL and RL-MLP have better times but poorer RPA. 

All LTR approaches are more affected by the 𝑇^2,code variability indicator. While all RL-based algorithms are more robust to variations, likely because of their online-learning nature. This suggests that in highly variable contexts, with intense metrics’ changes, RL-based approaches can be preferred, to avoid having to re-train a static LTR algorithm too often. In contrast, static contexts can stress the good performances of LTRs.


## Conclusions
A valuable approach under short inter-commit times is to run a ML prioritization algorithm after selection, so that it acts on a small problem size and on test cases relevant for that commit. An incremental static selection approach like the one experimented with appears suited for the time requirements of CI.

In the plethora of ML algorithms to choose from, a suggestion is to first decide the learning strategy and, possibly, the category (ensemble or non-ensemble), and then opt for the specific algorithm. The choice depends on the requirements for prioritization, in terms of desired ranking effectiveness and efficiency, tolerable sensitivity to code features, and on the CI process features. They are strongly dependent on the CI context.


## References
Bertolino, A., Guerriero, A., Miranda, B., Pietrantuono, R., & Russo, S. (2020). Learning-to-rank vs ranking-to-learn: Strategies for regression testing in continuous integration. Proceedings of the ACM/IEEE 42nd International Conference on Software Engineering, 1–12. https://doi.org/10.1145/3377811.3380369

Majid Babaei,(2023,Nov), Lecture16-CICD Pipeline, School of Continuing Studies, McGill University

















