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

# Topic#1 \[Taken]

Topic 1: [The Promises and Perils of Mining Git](https://ieeexplore.ieee.org/abstract/document/5069475)

{% hint style="warning" %}
This topic is taken by **Soumaia Bouhouia**!
{% endhint %}

“The Promises and Perils of Mining GitThe Promises and Perils of Mining Git” is a paper written in 2009 by Christian Bird\*, Peter C. Rigby†, Earl T. Barr\*, David J. Hamilton∗, Daniel M. German† and Prem Devanbu\* from the University of California (\*) and the University of Victoria (†).

Git, developed in 2005, was becoming increasingly popular at the time. This meant that more and more open-source projects were created on decentralized systems while, prior to that, most projects were hosted on centralized systems. This is significant on many levels, in particular in the domain of research as they may learn many things from a repository and its history. Here are 5 examples:

* They can reconstruct the process by which a software has been created. From that, some conclusions could be reached as to what steps developers go through to attain a publishable product, and the process could be made more efficient, thus gaining time and money.
* They can also study evolution patterns, meaning how a project is evolving as time passes.
* They can predict bugs.
* They can create recommender systems.
* They can explore collaborative processes.

As git was being used with increased frequency as time passed, it became important to determine whether the repositories created using Git would be as good for gathering data and performing analyses and how this analysis would need to change. Indeed, as we will see later, CSCM and DSCM systems like SVN (a centralized system) and Git (a decentralized system) have quite substantial differences that could either impede analysis or further facilitate it.

## **What is a CSCM system?**&#x20;

CSCM stands for Centralized Source Code Management system. In essence, developers connect to a central source or server to access the repository, and one of the main characteristics of this system is that changing a file leads to only the difference (delta) being stored. While CSCM systems have many benefits, especially in terms of security, the aforementioned properties complicate the retrieval of previous versions of the code if the code on the centralized server becomes corrupted \[3]. SVN (Apache Subversion) is one such system, and the authors of the paper compared it to Git, a DSCM system.

## What is a DSCM system?&#x20;

DSCM stands for Decentralized Source Code Management system. It enables developers to work independently on local repository copies, work offline while retaining access to the complete project history as well as create and merge branches at a minimal cost, and it enables them to commit individual changed lines within a file \[2].

DSCM data provides valuable insights for research. However, it also poses conceptual and practical challenges that are going to be expanded upon further in this summary. The paper's authors conducted a comparative analysis between SVN and Git, where SVN represents CSCM systems, while Git represents DSCM systems. They established a list of 9 promises Git makes, and compared the value of these promises with the perils Git was known to have at the time.

## Perils and Promises

In the following section, we examine the challenges associated with using Git, as identified by the authors. Each challenge is accompanied by a discussion of Git’s features that are instrumental in addressing these issues. The objective is to provide an informed and balanced perspective on how the features of Git counteract its identified shortcomings as described by the authors.

### Perils

1. **Git's Nomenclature:**
   * _**Description:**_ Git’s terminology differs significantly from traditional Centralized Source Code Management Systems (CSCMs). This distinction can create confusion and increase the learning curve for researchers wanting to perform analyses on Git.&#x20;
   * _**Mitigation (Promise 1 & 2):**_ Any developer can make their repository public, creating a richer learning environment. The detailed information on commits, branches, and merges stored in Directed Acyclic Graphs (DAGs) facilitates an intuitive understanding of Git’s unique nomenclature over time.
2. **Automatic Creation of Implicit Branches:**
   * _**Description:**_ Git’s mechanism of automatically creating implicit branches can lead to complexity and confusion.
   * _**Mitigation (Promise 2):**_ Git's detailed recording of project history, including branches and merges in DAGs, helps in visualizing and understanding the development of implicit branches, simplifying their management and navigation.
3. **Analysis Methods:**
   * _**Description:**_ The utilization of DAGs instead of a mainline necessitates different analysis methods, potentially complicating the tracking of changes and history.
   * _**Mitigation (Promise 2 & 3):**_ The detailed data in Git’s DAGs and private logs allow for the development of refined, Git-specific analysis methods, offering deeper insights than traditional mainline analyses.
4. **History Rewriting:**
   * _**Description:**_ The ability to rewrite Git history can potentially lead to data integrity issues.
   * _**Mitigation (Promise 4):**_ The “signed-off-by” and other attributes ensure a detailed “paper trail,” enhancing traceability and accountability, thus minimizing the risks associated with history rewriting.
5. **Branch Commit Identification:**
   * _**Description:**_ Determining the specific branch on which a commit was made can be challenging.
   * _**Mitigation (Promise 3 & 5):**_ Private logs and explicit recording of contributor information enhance traceability, making it easier to identify the origins of specific commits.
6. **Tracking Merges:**
   * _**Description:**_ It can be complicated to ascertain the occurrence and location of merges.
   * _**Mitigation (Promise 3):**_ The private logs in Git contain intricate details, assisting in tracking and identifying merges, ensuring clarity in the merging process.&#x20;
7. **Selective Commit Data:**
   * **Description:** Accessible data may only contain selected commits, leading to incomplete information.
   * _**Mitigation (Promise 1 & 6):**_ Having developers' repositories and metadata publicly accessible ensures a richer dataset, reducing problems caused by selective commit data.

### Further Insights on Promises

* _**Promise 7:**_ Git meticulously tracks file content and the history of lines, even as they are moved or copied, ensuring data integrity and providing detailed insights into the development of the codebase.
* **Promise 8:** Git is faster and uses less space than traditional SCMs.
* _**Promise 9:**_ Most SCMs can be easily converted to Git while keeping the history intact, facilitating the adoption of Git's robust features.

## Empirical Evaluations of Git’s Perils and Promises

On top of listing these perils and promises, the authors evaluated some of them through empirical analyses using real-world data.

#### Promise 5: Enhanced Author Tracking

The authors checked if Git's ability to track authors influenced the number of contributors in a project. They compared projects using SVN and Git. The data showed that Git led to a significant increase in contributors, thanks to its improved author tracking.

#### Peril 6: Tracking Merges

The completeness of merge information in Git was examined using 30 open-source projects. The findings showed that Git could identify almost all (97.9%) of the merge sources, indicating its effectiveness. However, the authors recommended more in-depth research for a thorough understanding.

#### Git's Impact on Workflow

The authors also investigated whether Git changes how developers work. They guessed that developers might make smaller, more frequent changes after switching to Git from a centralized system. Their analysis showed that while there was a statistically significant difference in commit size, it wasn't a major change.

#### Promise 4: Understanding Contributions

The authors studied Git log messages to understand individual roles and contributions in projects better. In the Linux kernel project, for example, a specific developer was found to be signing off on most commits in certain areas, highlighting their key role and expertise. This detailed data is helpful in understanding the distribution of work and expertise in a project.

## Research Inquiries

In concluding their paper, the authors present further questions to delve into the extensive effects of moving to decentralized SCM systems like Git and its influence on team interaction and project results.

* Does changing from a centralized to a distributed SCM system affect how the project team communicates or develops the project?
* Does adopting a DSCM system encourage more focused development while possibly diminishing awareness of the broader project?
* Do developer teams sometimes work together separately from the main repository for extended periods?

A 2014 paper titled “How Do Centralized and Distributed Version Control Systems Impact Software Changes?” touches upon the first question. It provides insights into the impact of DSCM systems like Git on software modification patterns. The study reveals that Git promotes more frequent, yet smaller commits, attributed to the ease of making detailed change selections and the absence of conflict concerns with local repositories. Interestingly, projects that moved from SVN to Git didn’t show a change in commit size or frequency, suggesting that established CSCM commit practices were retained.

Additional observations from this 2014 paper include:

* _**Observation 1:**_ Developers accustomed to CSCM systems expressed a preference for this workflow, attributing their comfort to familiarity rather than the system's features.
* _**Observation 2:**_ There is a slight indication that commit sizes may reduce as team size expands, although this observation isn't backed by substantial evidence.

These insights offer a nuanced perspective on the adaptive behaviors and preferences of developers in the context of centralized and distributed SCM systems.

## References

1. Bird, Christian, et al. “The Promises and Perils of Mining Git .” IEEE Xplore, 5 June 2009, ieeexplore.ieee.org/abstract/document/5069475.&#x20;
2. Brindescu, Caius, et al. “How Do Centralized and Distributed Version Control Systems Impact Software Changes?” ACM Conferences, 1 May 2014, dl.acm.org/doi/10.1145/2568225.2568322.&#x20;
3. Zolkifli, Nazatul  Nurlisa, et al. “Version Control System: A Review.” Procedia Computer Science, Elsevier, 29 Aug. 2018, www.sciencedirect.com/science/article/pii/S1877050918314819.

&#x20;
