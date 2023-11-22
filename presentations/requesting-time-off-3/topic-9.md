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


## Algorithms
![image](https://github.com/BirukBerhanuRetta/ECSE437/assets/96294628/ebabbbfb-3b11-4b68-b0ee-0ddc500d572d)

The LTR strategy can use pointwise, pairwise or listwise algorithms 
Pointwise LTR. The ranking problem is transformed into classification, regression, orordinal classification, and solved with respective existing methods. The training data are typically supervised learning data; given a sample(a test target), the algorithm predicts the class label, real number or grade label for the three cases.For example, in classification problems the score can be the probability of a test belonging to a class (e.g., high-priority and low-priority, in a binary formulation); in regression and ordinal classification problems, a function of the testing objective yielding a real priority number or a grade. The loss function in learning is pointwise in the sense that it is defined on a single object (featurevector).

PairwiseLTR Ranking is transformed into a classification or regression problem, where a sample is a pair of test targets: a model can tell which test target has higher score than the other in a pair. The goal is to minimize the average number of inversions in ranking, due to unordered pairs.

ListwiseLTR. The problem is addressed in an intuitive way, as ranking lists are taken directly as samples in both learning and prediction.The approach trains a model able to assign scores to feature vectors and rank them accordingly. The goal is to minimize the difference between the predicted and the actual ranking lists. 
In classification-based pointwise LTR, we consider four classes derived from the two above-mentioned prioritization criteria(fault detection and execution time), which are (in decreasing priority): 
Class3: At least one failure is detected running the test target, and the execution time of the test target is shorter than a threshold (computed as the median of execution times on the last W samples); 
Class2:Atleast one failure is detected running the test target, and its execution time is longer than the threshold;
Class1: No failure is detected running the test target, and its execution time is shorter than the threshold;
Class0: No failure is detected running the test target, and the execution time of the test target is longer than the threshold.

This work evaluates the ten algorithms listed in the table above. They can be further classified into ensemble and non-ensemble algorithms: the former category includes: RF, RL-RF, RankBoost, MART, L-MART;  the others are non-ensemble. The Weka 4 and Knime 5 tools were used for point wise algorithms, and the RankLib library for pairwise and listwise algorithms. The number of samples used for training, initially set to 2,000, is subject to sensitivity analysis.

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

Inter-committime. RPA measured algorithms’ performance regardless of the time available to execute test cases. If time limits do not allow to run all selected tests, the tester might be interested in analyzing the algorithms’ performance under various time constraints. Based on a previous work studying regression testing under different time constraints, they consider scenarios in which 25%, 50% and 75% of the number of selected tests can be run at each cycle, and assess the impact on ranking effectiveness.

Whenever results are in line with the RPA, e.g., L-MART and MART on test execution times or RankBoost on number of failures that are close to the optimal one, it means that mis-ranked tests had low impact (e.g., because their execution times or number of failures is not much different than those of the optimal ranking’s tests). When results are not in line with RPA, e.g., RL-RF and RankNet on failures, then either the algorithm performs well for one prioritization criterion and bad for the other and/or the tests that were mis-ranked, even by a small amount, had a high impact. Clearly, short inter-commit time may influence the choice of the algorithm to adopt more than the RPA metric.

History length. They investigate whether and to what extent the amount of history used for learning impacts performance of the algorithms. For LTR, this history is used just once at the beginning for training; for RTL, the history is in a sliding window (the memory) used to update the learning process online.   The RPA is quite insensitive with respect to a training sample size bigger than 500 observations,for all the algorithms. The average good performance of LTR even with smaller training sets mitigates the draw back of not having predictions during the training process. Contrarily, the training time expectedly increases remarkably with training sample size (the graph is in logarithmic scale): the RTL algorithms are severely affected,followed by pairwise and listwise, and finally, the least affected ones, the point wise algorithms.


## Conclusions
A valuable approach under short inter-commit times is to run a ML prioritization algorithm after selection, so that it acts on a small problem size and on test cases relevant for that commit. An incremental static selection approach like the one experimented with appears suited for the time requirements of CI.

The testing criteria should be identified first, along with their relative weight within the ranking function : they determine what the optimal ranking is. If a coarse -grain ranking is enough, then classification algorithms may workwell; otherwise, regression approaches better manage fine-grain ranking problems. Most of the experimented algorithms can work with both formulations. 

The ML algorithm’s input consists of the features more likely related to the identified testing criteria. We targeted feature selection in an algorithm-independent way (unsupervised), first defining relevant features and then choosing the algorithm based on other requirements–this simplifies the problem. An alternative is to run feature selection for each potential algorithm being considered, so as to infer the best features for each of them: this, although more precise, can be much more time-consuming.
In the plethora of ML algorithms to choose from, a suggestion is to first decide the learning strategy and, possibly, the category (ensemble or non-ensemble), and then opt for the specific algorithm. The choice depends on the requirements for prioritization, in terms of desired ranking effectiveness and efficiency, tolerable sensitivity to code features, and on the CI process features. They are strongly dependent on the CI context.


## References
Bertolino, A., Guerriero, A., Miranda, B., Pietrantuono, R., & Russo, S. (2020). Learning-to-rank vs ranking-to-learn: Strategies for regression testing in continuous integration. Proceedings of the ACM/IEEE 42nd International Conference on Software Engineering, 1–12. https://doi.org/10.1145/3377811.3380369

Majid Babaei,(2023,Nov), Lecture16-CICD Pipeline, School of Continuing Studies, McGill University

















