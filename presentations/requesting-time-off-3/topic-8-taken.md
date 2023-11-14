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

# Topic#8 \[Taken]

Topic 8: [The Impact of a Continuous Integration Service on the Delivery Time of Merged Pull Requests](https://arxiv.org/abs/2305.16365)

{% hint style="info" %}
This topic is taken by **Ningning Yang**!
{% endhint %}

Full presentation: [ecse437_topic8_Ningning_Yang.pdf](https://github.com/Ningning-Yang/Ningning-Yang/blob/94cf11611e9f6edc318ff8902407142d1667309f/ECSE437_CI_in_Software_Development.pdf)

## Introduction & Background

Introduction
- Overview of CI:
  - CI, as highlighted in the paper, is a software development practice involving the automatic integration of code changes into a shared repository.
  - Emphasizes automated testing, aiming to detect and address issues early in the development process.
- Motivation:
  - The paper emphasizes the motivation behind CI adoption as a means to quicken the delivery of merged Pull Requests in software projects.
  - The focus is on understanding how CI impacts the software development lifecycle, specifically in terms of PR processing and delivery time.
- Significance:
  - While the adoption of Travis CI, a CI service, doesn't universally accelerate the delivery of merged PRs, the study reveals crucial insights.
  - CI, as a practice, significantly influences the decision-making processes of software projects, affecting code review and release procedures.
  - Automation and increased confidence are identified as key benefits, impacting project throughput and contributor engagement.

Background of Study
- The study focused on 87 GitHub projects employing TRAVISCI as their chosen CI service.
- TRAVISCI is known for automating builds and testing processes upon code changes.
- Quantitative Analysis
  - Investigated the impact of TRAVISCI on the delivery time of merged pull requests across these projects.
  - Examined factors influencing the effectiveness of CI using a vast dataset of 162,653 pull requests.
- Qualitative Insights
  - Complemented the quantitative aspect with a qualitative study, tapping into the perceptions of contributors involved in 73 of these projects.
  - Explored how CI influences code reviews, release processes, and the attraction of external contributors.



## Quantitative Study
Questions: 
- Q1: Are merged pull requests released more 
quickly using a CI service?
- Q2: Does the increased number of PR submissions after adopting a CI service increase the delivery time of pull requests?
- Q3: What factors impact the delivery time after adopting a CI service?

Findings:
- Q1: Only 51.3% of projects showed quicker delivery of merged PRs after adopting TRAVISCI.
- Q2: 54% of projects experienced longer PR lifetimes after CI adoption.
- Q3: Increased PR submissions and merge workload were significant factors affecting delivery time​​.

## Quanlitative Study
Questions:
- Q4: What is the perceived influence of CI on the time to deliver merged PRs?
- Q5: What are the perceived causes of delay in the delivery time of merged PRs?
- Q6: What is the perceived influence of CI on the software release process? 
- Q7: What is the perceived influence of CI on the code review process? 
- Q8: What is the perceived influence of CI on attracting more contributors to open-source projects?

Findings:
- Q4: 
  - Participants expressed mixed views regarding the impact of CI on the delivery time of merged PRs. 
  - While some noticed an improvement in delivery speed, others did not observe significant changes. 
  - This aligns with the quantitative finding that only about half of the projects experienced quicker delivery post CI adoption​​.
- Q5: 
  - Contributors often cited increased complexity and volume of PR submissions as contributing factors to delays in delivery time. 
  - This observation is consistent with the quantitative result showing an increase in PR lifetime in 54% of the projects after adopting CI​​.
- Q6: 
  - Many respondents felt that CI facilitated a smoother release process by enabling more consistent and automated testing. 
  - However, they also noted that this did not necessarily translate to an increased release frequency, as the study's quantitative results similarly indicated​​.
- Q7:
  - Participants reported that CI helped streamline the code review process by automating certain checks, leading to more focused and efficient reviews. 
  - However, the faster merging of PRs before CI adoption in 73% of projects suggests that CI's role in speeding up the review process is complex​​.
- Q8: 
  - Contributors believed that the adoption of CI practices made the project more appealing to potential new contributors by demonstrating a commitment to modern development practices and ensuring code quality.
  - This qualitative insight complements the quantitative finding that 75.9% of projects saw an increase in the number of contributors post CI adoption​​.

## Implications
Practical Implications for Software Teams

- Considered CI Adoption: 
  - Teams should adopt CI services like TravisCI with a clear understanding of their potential and limitations. 
  - While CI can improve aspects of the development process, it may not always speed up the delivery time of PRs. Teams should evaluate how CI aligns with their specific project needs and workflows​​.

- Focus Beyond Speed: 
  - The findings suggest that the benefits of CI extend beyond just delivery speed. 
  - CI can enhance decision-making processes, improve code quality, and facilitate handling a larger volume of contributions. 
  - Teams should leverage these advantages while being aware that delivery speed may not be significantly impacted​​.

- Adaptation to Increased Workloads: 
  - With the adoption of CI, teams might face an increased number of submissions, leading to longer PR lifetimes. 
  - Software teams should prepare for this potential increase in workload and consider strategies to manage it effectively​​.

- Quality over Quantity: 
  - The study suggests that a strategic focus on quality and efficient management of PRs could be more beneficial than simply aiming for speed. 
  - Teams should prioritize maintaining high-quality code and effective review processes over merely expediting PR delivery​​.

- Shorter Release Cycles: 
  - To optimize the delivery process, teams might consider adopting shorter release cycles. 
  - The study indicates that merged PRs have a lower delivery time when they are merged more recently in the release cycle​​.

## The Validity & Limitation of Study

Validity of the Study
- Comprehensive Data Analysis: 
  - Utilized a large dataset of 162,653 pull requests from 87 GitHub projects, ensuring a broad and diverse sample.
- Mixed-Methods Approach: 
  - Combined quantitative and qualitative research methods, providing a well-rounded perspective.
- Empirical Evidence: 
  - Offered empirical evidence to support findings, enhancing the study's credibility.
- Relevance to Current Practices:      
  - Addressed a highly relevant topic in modern software development, making the findings applicable and timely.

Limitations of the Study

- Focus on TravisCI Only: 
  - Limited to projects using TravisCI, not encompassing other CI tools which might yield different results.
- Restricted to GitHub Projects:  
  - Exclusively analyzed GitHub projects, potentially missing insights from projects hosted on other platforms or in private repositories.
- Potential Biases in Survey Responses: 
  - Reliance on self-reported data in surveys could introduce subjective biases.
- Open-Source Project Emphasis: 
  - Primarily addressed open-source projects, which may not completely represent the dynamics in closed-source or commercial software environments.
- Generalizability Concerns: 
  - The findings might not be entirely generalizable to all software development contexts due to the specific focus and sample used in the study.

## Conclusions
The study on the impact of CI services like TRAVISCI on the delivery time of merged PRs offers new insights that challenge prevailing assumptions in software development. 

While CI brings several advantages, its impact on speeding up PR delivery is not as straightforward as often believed. 

Teams must approach CI adoption with a nuanced understanding, focusing on its broader benefits and preparing for potential increases in workload. By doing so, they can effectively harness CI to enhance their software development processes.

## Reference
Bernardo, J. H., da Costa, D. A., Kulesza, U., & Treude, C. (2023). The impact of a continuous integration service on the delivery time of merged pull requests. Empirical Software Engineering, 28(4). https://doi.org/10.1007/s10664-023-10327-6 