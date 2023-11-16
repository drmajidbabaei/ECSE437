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

# Topic#10 \[Taken]

Topic 10: [Uncovering the benefits and challenges of continuous integration practices](https://ieeexplore.ieee.org/abstract/document/9374092/?casa\_token=H\_di3ZkRu8EAAAAA:DMlJXJhRcj-oXiFAIJBJzB\_Ybrevi\_d2t7ivneiGAOtJLZUmmJoU\_IeL-Btf\_Qn8epgEz0gX)

{% hint style="warning" %}
This topic is taken by **Abraham Somech, Liam Serour**, and **Samuel Vasserman**
{% endhint %}

## Introduction ##
The paper starts off by defining Continuous Integration (CI). CI involves iteratively integrating small changes into a codebase, supported by tools and processes for rapid feedback and quality improvement. As its name suggests, CI focuses on keeping the code and contributors integrated and on the same page. The study examines the implementation of ten core CI practices defined by Fowler and Foemmel in 2006, exploring how these practices are adopted, their advantages and disadvantages, and the challenges they pose in different organizational contexts.

## CI Practices ##
1. Maintaining a Single Source Repository
2. Automating the Build
3. Making Builds Self-Testing
4. Daily Commits to the Mainline
5. Ensuring Each Commit Builds on an Integration Machine
6. Keeping the Build Fast
7. Testing in a Production-like Environment
8. Easy Access to the Latest Executable
9. Visible System State and Changes
10. Automated Deployment

The paper outlines the advantages and disadvantages of each of these practices. It then discusses how these practices are widely adopted but vary in implementation depending on context and perceived benefits.

## Methodology ##
The methodology used in the study of Continuous Integration (CI) practices was essentially split into two categories. Four of the practices can be quantified and thus they were analyzed by data-driven analysis without needing to speak with workers at the companies. For the other practices, it was necessary to conduct interviews and speak to workers in order to understand how the practices were being adopted. 

Data-Driven Analysis:

Data-driven analysis focused on CI practices that could be quantitatively measured and thus observed directly from CI artifacts. This included practices that have a direct output (visibility) in the software development process. The specific CI practices studied through data-driven analysis include:
Automating the Build: This practice could be studied through data-driven analysis by examining the build logs to check if automated builds are used or not. 
Daily Commits to the Mainline: By looking at the trace logs, it is possible to see the commit history. However, some of the commit history was lost due to commits that were squashed for instance.
Ensuring Each Commit Builds on an Integration Machine: This could be studied by looking at the repository activity to see if the commit resulted in a build by looking at the build status indicator. 
Keeping the Build Fast: Build logs could be used to analyze the duration of each build, assessing whether the builds are being kept fast. 

Interviews for Understanding Adoption:

The other CI practices cannot be studied from data alone. For instance, determining if changes have visible state changes is something that needs to be verified by speaking to workers. In order to do this, many different organizational members from the companies were interviewed. The interviews were conducted by using open-ended questions and asking the participant to elaborate on things. 

## Findings ##
The organizations varied in their adoption and implementation of CI practices due to differences in project context, practice perceptions, and process constraints. Before delineating the main findings, the paper explains the organization profiles, which will give insight to why there were differences in implementation. 

Organization Profiles:

Organization A: does data processing and deals with projects that involve large data volumes and complex processing requirements. Their CI practice implementations would reflect the need to handle these data-centric tasks efficiently.

Organization B: An online content provider, using its publishing platform, such as advertisement management. Recognized for their structured, automated workflow and strong commitment to CI practices.

Organization C: Specializing in online bookings, this organization's projects would involve integrating multiple services for a global customer base. The CI practices here would be aimed at ensuring robustness and reliability across various integrated systems.

Differences in CI Practice Implementation:

**Maintaining a Single Source Repository:**

Organization A prioritizes the reduction of merge conflicts in their development process. To achieve this, they have structured their repository by separating components based on the need for simultaneous updates. This approach is specifically designed to minimize conflicts that arise when multiple components are updated concurrently, reflecting their strategic focus on maintaining a smooth and conflict-free development workflow.

Organization B opts for a distinct approach where each component is maintained in its own separate repository. The rationale behind this structure stems from their inability to see the clear benefits of a monolithic repository, commonly known as a mono repo. However, this decision necessitates duplicating their workflow processes and maintaining complex dependency graphs between components. This structure could potentially introduce increased overhead and complexity in their development process, highlighting a trade-off in their repository management strategy.

Organization C initially adopted a single repository structure, driven by workflow considerations. However, they later transitioned to branching off different parts of their project into separate repositories. This shift was primarily due to limitations in their tooling capabilities. The tools at their disposal may not have been adequately equipped to manage a large, integrated codebase efficiently, prompting them to modify their repository structure. This evolution in their approach underscores the impact of tooling on repository management decisions and the need to adapt to technical constraints.

**Making the Build Self-Testing:**

In software engineering practice, different organizations prioritize various aspects of their development processes based on their unique perspectives and resource allocations. Organization A, for instance, emphasizes the importance of faster build times prior to the pull request (PR) stage, coupled with a strategy where lengthier, more comprehensive tests are conducted during the review phase. This approach is rooted in person 1 who expresses a preference for minimizing the duration of tests conducted on the developer's side, thereby optimizing the developers' time and efficiency. On the other hand, Organization B prioritizes financial resources over the development of their infrastructure. Organization C places a higher value on thorough testing, even if it results in longer build durations. This reflects a commitment to quality and reliability in their software products, demonstrating how organizational priorities can significantly influence the balance between speed, efficiency, and thoroughness in software development methodologies.

**Keeping the Build Fast:**

The duration of builds is a critical factor that varies significantly across different organizations. This is influenced by their specific priorities and operational contexts.

Organization A aims to keep most of their builds quick. They recognize the advantage of reducing the problem of context switching for developers. Rapid builds enable developers to stay focused on their current task without significant interruptions. However, some builds in this organization may take longer, particularly in scenarios involving extensive data processing. This indicates a nuanced approach where the build duration is adapted based on the specific needs and context of the project, balancing speed with the demands of complex tasks.

Organization B has streamlined their process to ensure that builds take no longer than 10 minutes. This brings two key benefits: it minimizes context switching, allowing developers to maintain a high level of concentration and efficiency, and it reduces blocking in the development process, ensuring that team members are not left idle waiting for builds to complete. This approach reflects a strategic emphasis on maintaining a high tempo in development cycles and optimizing developer productivity.

Organization C experiences build durations ranging from 10 to 20 minutes. This longer build time is influenced by two main factors: a higher priority placed on thorough testing and certain infrastructure limitations. The organization’s decision to prioritize comprehensive testing over build speed underscores a commitment to quality and reliability, even at the expense of longer build times. The infrastructure limitations further contribute to these extended durations, indicating a potential area for future improvement or investment.

**Automating Deployment:**
In the context of deployment processes, all three organizations have opted for manual triggering for deployments. However, each company had a distinct approach in doing so that reflects their culture and hierarchy. Organizations A and C reserve this privilege for senior members, ensuring that deployment decisions are made by experienced personnel, preventing indiscriminate deployment by less experienced team members. This approach emphasizes a controlled and hierarchical decision-making process. In contrast, Organization B adopts a different approach, assigning the responsibility of deployment to the developer who authored the change. This strategy is rooted in the rationale of fostering a culture of ownership, where developers are directly accountable for the changes they implement. This approach encourages developers to be more thorough and responsible, as they are directly involved in the deployment of their own work, promoting a sense of ownership and responsibility within the team.


## Discussion: ##
The study found that variation in implementation practices of CI practices are related to the following themes: differences related to project context, practice perception and CI-related process constraints. The context of the project clearly has an impact as we saw. For instance, if there is a lot of data for testing, then of course the tests will take longer. The practice perception also had a large impact. Some organizations viewed testing as detrimental when it is too long and made a decision to keep it short due to that. Regarding CI related process constraints, it is crucial to keep in mind that the goal of CI is to speed up the development feedback cycle. However, integrating CI practices can sometimes lead to increased cycle times. For instance, waiting for other pull requests (PRs) to be completed before proceeding with merging. This ensures better integration and consistency but it also slow down the cycle by blocking merges if there is a backlog of PR’s. These variations challenge the notion of CI as a uniform set of practices, and the need for a nuanced understanding of CI in different contexts to apply them properly.

## Conclusion ##
The study concludes that CI is not something black on white where we can definitely say whether a company follows it or not. Instead, CI should be viewed as a spectrum that must be tailored to specific organizational contexts and needs. The degree to which CI is adopted is influenced by various factors such as project type, testing strategy, and organizational perception. Understanding these nuances is crucial for both researchers and practitioners to understand why CI is being used in a particular way in a company and how it should be used. 	

## References ##				
Elazhary, O., Werner, C., Li, Z. S., Lowlind, D., Ernst, N., & Storey, M.-A. (2021, March 7). Uncovering the benefits and challenges of continuous integration practices. arXiv.org. https://arxiv.org/abs/2103.04251 
M. Fowler and M. Foemmel, “Continuous integration,” 2006, Accessed: May 21, 2020. [Online]. Available: https://tinyurl. com/ycbl2uhj 
 						 					
M. Fowler and M. Foemmel, “Continuous integration,” 2006, Accessed: May 21, 2020. [Online]. Available: https://tinyurl.
com/y8d3asjv
				 							
M. Heller, “Continuous integration: The answer to life, the uni- verse, and everything?,” 2015, Accessed: Jul. 14, 2020. [Online]. Available: https://tinyurl.com/y8rhxnt8 
	
 D. Stahl and J. Bosch, “Experienced benefits of continuous integration in industry software product development: A case study,” in Proc. 12th IASTED Int. Conf. Softw. Eng., 2013, pp. 736–743. 