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

# Topic#3 \[Taken]

Topic 3: [Modern code review: a case study at Google](https://dl.acm.org/doi/abs/10.1145/3183519.3183525)

{% hint style="warning" %}
This topic is taken by **Zach Hayden**
{% endhint %}


Full presentation: [ecse437_topic3_Zachary_Hayden.pdf](https://github.com/zachary0249/ECSE437/files/12819414/ecse437_topic3_Zachary_Hayden.pdf)

Citation: Caitlin Sadowski, Emma Söderberg, Luke Church, Michal Sipko, and Alberto Bacchelli. 2018. Modern code review: a case study at google. In Proceedings of the 40th International Conference on Software Engineering: Software Engineering in Practice (ICSE-SEIP '18). Association for Computing Machinery, New York, NY, USA, 181–190. https://doi.org/10.1145/3183519.3183525

## Summary
1. Introduction

   * The paper aims to address the current state of code review by taking a deep dive into Google's operations which have allowed them to scale to where they are today. Originally, code review was a very tedious and synchronous process wherein developers (including the author) would gather to discuss their code line by line with the goal of detecting erros in the code. This approach created more logistical and resource overhead. What the authors found to be the modern approach for code review, and a workflow that google had employed, was to use tooling to automate tasks and create organized ways of contributing asynchronously. This way, developers could review the code on their own time and not all together allowing for improved efficiency. Additionally, instead of reviewing code line by line they instead look only at the areas in which changes have been made. A common example of this that surrounds us in all types of development environments is the use of git pull requests which provide a means for teams to be able to review code seperately and communicate via comments to address issues.
   * What motivated Google's code reviews weren't soley to identify errors in the program which had been the norm in the original code review construct, but instead the main focus was on the readability of the code base especially as it was rapidly growing. The reason for this the authors found was that the original Google developers wanted the code base to act as a strong education tool for the vast amounts of developers they would employ; by ensuring uniform code styling, making developers be language certified internally before being able to commit, and creating small commits, allowed Google to accomplish just that.
   * Google made two key concepts vital for their code review: ownership and readability. Ownership in the sense that each directory is "owned" by a set of developers and this set were primarily in charge of writing and reviewing the changes made to their directory but only after these developers were trusted from a readability standpoint.

3. Approach

    * The authors took a three-pronged approach for their research methods in order to extract what it is that defines Google's modern code review practices.
      1. Semi-structured interviews with Google developers
      2. Logs from Google's internal code review tool called Critique (only considering commits with more at least 1 additional reviewer)
      3. Survey to Google employees who had recently made commits to gauge their perspective on the effectiveness of the process and how they feel it went for their most recent code change.

4. Results
  
    * 80% of developers make < 7 changes a week
    * Median developer makes 3 changes a week and
  reviews 4
    * 80% of reviewers audit < 10 changes a week
    * Median latency for entire code review is < 4
  hours
    * 35% of edits only modify one ﬁle
    * Median number of lines modiﬁed in a change =
  24
    * < 25% of changes receive more than one
  reviewer
    * 70% of edits are committed within a day of
  being published for initial review
  
    * The authors identified key themes that were shown to cause friction in the process which were: 
      1. distance
  
          > Distance is a challenge that many people are familiar with notably
  in the last couple years with covid. Being physically far from
  someone reviewing your code reduces streamlined communication
  pathways. Additionally inter-department reviews can pose as a
  distance of sorts where expectations and norms are different.
  
      2. social interaction dynamics
  
          > Social interactions of any type give rise to potential character
  conﬂicts such as using a demeaning tone or trying to exert their
  power / authority in a review exchange. This leads to overall
  frustration and reduced productivity.
  
      3. subject matter
  
          > Discrepancies in what each party thought the topic of discussion is
  can also lead to ineﬃciencies in the process. This is why it’s
  essential to clearly state the intention of the review especially for
  design reviews.
  
      4. context of review
  
          > There are varying levels of necessity for making a change and
  misunderstanding around the severity can cause communication
  problems.
  
      5. cusomtization / configuration
  
          > Differences in configurations and standards between ownership groups caused certain issues when cross-team collaboration was required. For example, when one team that required two reviewers had to collaborate with a team that required a number less or greator, there were disputes because of this miscommunication.

5. Takeaways and discussion

   * Lighter is better
     
       * Having only 1 reviewer improved productivity
       * Much more efficient than original code inspections
   * Less is more

       * Having more frequent but less cumbersome commits is better for streamlining the entire process from edit to commit
       * Large edits reduce quality of comments from reviewers and lengthens the code review process overall

   * Reviewer recommendation systems are important in making sure that the code review process is effective as it is important to have someone who is familiar with the codebase to ensure that the changes proposed aren't harmful; these systems are an active area in current and ongoing research
   * Static analysis integration is the most requested feature for code review tools according to data pulled by the authors
   * Code review tools serve more purposes than just for code review alone, they can also provide meaningful data about the progress of the project during its development that can benefit developers as they work.


#### References
[1] Rachel Potvin and Josh Levenburg. 2016. Why Google StoresBillions of Lines of Code in a Single Repository.Commun. ACM(2016).
[2] A.F. Ackerman, L.S. Buchwald, and F.H. Lewski. 1989. Softwareinspections: An effective verification process.IEEE Software6,3 (1989), 31–36.
[3] A.F. Ackerman, P.J. Fowler, and R.G. Ebenau. 1984. Softwareinspections and the industrial production of software. InSym-posium on Software validation:
inspection-testing-verification-alternatives.
[4] M.E. Fagan. 1976. Design and code inspections to reduce errorsin program development.IBM Systems Journal15, 3 (1976),182–211.
