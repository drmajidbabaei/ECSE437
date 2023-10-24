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

# Topic#4 \[Taken]

Topic 4: [Who Should Review My Code?](https://ieeexplore.ieee.org/abstract/document/7081824?casa\_token=6Z91gNG9zNIAAAAA:Z04ELyR7TMVN2rDI5q0HGnceQ7Y19xWl8eHdXorMDtfsP7hYd3PfN1G5MfEgf-Gem\_4OUBFh)

{% hint style="warning" %}
This topic is taken by **Alexa Vasilakos**
{% endhint %}

## Overview of the Paper

“Who should review my code? A file location-based code-reviewer recommendation approach for Modern Code Review” is a research paper by Patanamon Thongtanunam, Chakkrit Tanithamthavorn, Hajimu Iida and Ken-ichi Matsumoto from the Nara Institute of Science and Technology, Raula Gaikovina Kula from Osaka University, and Norihiro Yoshida from Nagoya University. The paper was published in the 2015 IEEE 22nd International Conference on Software Analysis, Evolution, and Reengineering (SANER) which ran from March 2nd – 6th, 2015. The paper was added to IEEE Xplore on April 9th, 2015.

The authors aimed to address the following problem:

_“Finding appropriate code-reviewers is a necessary step in modern code review (MCR), however little research is known on the difficulty of finding appropriate code-reviewers in distributed software development and its impact on reviewing time.”_

The researchers wished to tackle a problem known as the “Code-Reviewer Assignment Problem.” They proposed a technology called REVFINDER, which is a file location-based code-reviewer recommendation approach that leverages previously reviewed file paths to determine and recommend appropriate code-reviewers.

\


## The Code-Reviewer Assignment Problem

The Code-Reviewer Assignment Problem is one of the main problems the researchers aimed to address. It refers to when an individual cannot find appropriate reviewers for their change request (we say that person has a “code-reviewer assignment problem”). In a Gerrit-based code-review system, a reviewer can either be identified as a “code-reviewer” or a “verifier”.

A **Code-reviewer** discusses the proposed change and suggests fixes.

A **Verifier** executes tests to ensure that the patch either fixes a defect or properly adds the feature that the owner of the change claims, and that the patch doesn’t cause regression of system behaviour.

Changes made by an owner will be integrated into the repository and marked as “Merged” if and only if it receives a code-review score of +2 (Approved) from a code-reviewer and it receives a verified score of +1 (Verified) from a verifier. In the Android example provided by the researchers, they depicted an owner (Smith) who was having trouble finding a code-reviewer for his change request, tasking his verifier (John) with finding one. Thus, it was concluded that Smith has a code-reviewer assignment problem.

\


## An Overview of REVFINDER

REVFINDER is a solution proposed by the researchers that leverages a similarity in previously reviewed file path to determine appropriate reviewers. The intuition is that “files located in similar paths would be managed and reviewed by similar experienced code-reviewers.”

The solution is composed of two parts: the **Code-Reviewers Ranking Algorithm** and the **Combination Technique**.

### 1. The Code-Reviewers Ranking Algorithm

This algorithm computes code-reviewer similarity scores via a similarity of previously reviewed file path. Given a new review as input, and a list of previously closed reviews, the algorithm will calculate a review similarity score for each of the previous reviews with the new review by comparing file paths using string comparison techniques. The scores are distributed to the code-reviewers involved, and the algorithm outputs a list of code-reviewers along with their scores.

The following four string comparison techniques were used. Underneath each technique is the assumption given by the researchers.

#### Longest Common Prefix (LCP)

**Assumption:** files under the same directory would have similar or related functionality.

#### Longest Common Suffix (LCS)

**Assumption:** files having the same name would have the same functionality.

#### Longest Common Substring (LCSubstr)

**Assumption:** since file path represents functionality, the related functionality should be under the same directory structure however, the root directories or filenames might not match.

#### Longest Common Subsequence (LCSubseq)

**Assumption:** files under similar directory structure would have similar or related functionality.

### 2. The Combination Technique

Due to variants in string comparison technique, REVFINDER combines the different lists into a unified list of code-reviewers with the idea being that truly relevant code-reviewers will “bubble up” to the top. **The Borda Count method** was used as the combination technique.

\


## Research Questions

The researchers aimed to address three research questions however, for the sake of time and relevance, I chose to explore research questions 2 and 3 in greater detail.

### Research Question #2:

_“Does REVFINDER accurately recommend code-reviewers?”_

### Research Question #3:

_“Does REVFINDER provide better ranking of recommended code-reviewers?”_

\


## Evaluation Methods

### 1. Studied Systems

REVFINDER was evaluated using four open-source software systems: Android (AOSP), OpenStack, Qt by Digia Plc., and LibreOffice. These systems were chosen by the researchers for two reasons: they use Gerrit for their code review system, and these are active real-world software systems that allow the authors to provide a realistic evaluation on REVFINDER.

### 2. Metrics

* Top-k accuracy
  * Calculates the percentage of reviews that an approach can correctly recommend code-reviewers and the total number of reviews
  * eg. a top-10 accuracy value of 75% indicates that for 75% of the reviews, at least one correct code-reviewer was returned in the top-10 results
* Mean Reciprocal Rank (MRR)
  * Calculates an average of reciprocal ranks of correct code-reviewers in a recommendation list

### 3. REVIEWBOT – REVFINDER’s baseline

REVIEWBOT is another code-reviewer recommendation technology that operates off the assumption that “the most appropriate reviewers for a code review are those who previously modified or previously reviewed the sections of code which are included in the current review.” REVIEWBOT looks at line-by-line modification history to recommend code-reviewers.

\


## Results

### Research Question #2:

_“Does REVFINDER accurately recommend code-reviewers?”_

#### Approach:

For each studied system, REVFINDER was run on all reviews in chronological order to obtain the lists of code-reviewers, top-k accuracy was calculated, and results were compared against REVIEWBOT.

#### Result:

On average, for 79% of reviews, REVFINDER correctly recommended code-reviewers with a top-10 recommendation. REVFINDER ended up being 4 times more accurate than REVIEWBOT.

### Research Question #3:

_“Does REVFINDER provide better ranking of recommended code-reviewers?”_

#### Approach:

Mean Reciprocal Rank (MRR) was used to represent the overall ranking performance of REVFINDER, and results were compared against REVIEWBOT.

#### Result:

REVFINDER recommended the correct code-reviewers with a median rank of 4. The overall ranking of REVFINDER ended up being 3 times better than that of REVIEWBOT.

\


## Discussion

### Performance

_“Why does REVFINDER outperform REVIEWBOT”_

REVFINDER and REVIEWBOT are different when it comes to the granularity of code-review history, with REVFINDER leveraging file-path similarities and REVIEWBOT leveraging line-level similarities. The authors observed that 70% - 90% of lines of code are changed only once, concluding that line-level code review systems such as REVIEWBOT lack in performance.

### Applicability

_“Can REVFINDER effectively help developers find code-reviewers?”_

An exploratory study was performed where a representative sample of reviews was selected and then analyzed in order to identify which of them had code-reviewer assignment problem. The results of the study showed that reviews with code-reviewer assignment problem required more time to investigate the change. REVFINDER was executed on the reviews with code-reviewer assignment problem from the samples and found that on average, it correctly recommended code-reviewers for 80% of the reviews with a top-10 recommendation.

### Threats to Validity

#### Internal Validity

**Threat:** The reviews classification process was conducted by authors not involved in the code-review system.\
**Impact:** Since the classification process was conducted by authors not involved in the code-review system, this could be considered a threat, as they have decreased domain knowledge.

#### External Validity

**Threat:** The results are limited to four datasets (Android, OpenStack, Qt, LibreOffice).\
**Impact**: Limiting sample size in this way doesn’t give us the full picture, despite the fact that these systems were chosen due to their relevancy and high usage. Having a larger sample size provides a more realistic outcome on REVFINDER’s performance.

#### Construct Validity

**Threat:** Lack of code-reviewer retirement information.\
**Impact:** There’s is not enough information on code-reviewers who are retired or no longer involved in the code-review system. This can impact results greatly, as we might be recommended fantastic code-reviewers for the job, but they are no longer present. Thus, we have an inaccurate picture of which code-reviewers are truly available.

**Threat:** Code-reviewer workload.\
**Impact:** How can we measure how busy a code-reviewer is? It’s entirely possible that there’s a highly-ranked code-reviewer that often gets recommended by REVFINDER and is therefore burdened with many assigned reviews. Workload balancing would be a future consideration and optimization for REVFINDER.

\


## Future Work

The authors hope to deploy REVFINDER in a real development environment and perform experiments with developers to analyze the efficiency and practicality of REVFINDER in the workplace.

\


## Works Cited

P. Thongtanunam, C. Tantithamthavorn, R. G. Kula, N. Yoshida, H. Iida and K. -i. Matsumoto, "Who should review my code? A file location-based code-reviewer recommendation approach for Modern Code Review," 2015 IEEE 22nd International Conference on Software Analysis, Evolution, and Reengineering (SANER), Montreal, QC, Canada, 2015, pp. 141-150, doi: 10.1109/SANER.2015.7081824.

GitLab. “What Is a Code Review?” GitLab, about.gitlab.com/topics/version-control/what-is-code-review/.
