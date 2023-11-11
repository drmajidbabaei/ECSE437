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

# Topic#5 \[Taken]

Topic 5: [Developing docker and docker-compose specifications: A developers' survey](https://ieeexplore.ieee.org/abstract/document/9658534/)

{% hint style="warning" %}
This topic is taken by Sandy Nguyen, Minna Feng, and Béatrice Duval!
{% endhint %}

## 1. Introduction

Infrastructure as Code (IaC) is the practice of managing and provisioning infrastructure resources using code and automation instead of a physical hardware setup. In other words, it is about treating your computer infrastructure as something you can create, manage, and change using code. 

IaC, especially with containers like Docker, has become popular due to cloud computing and the growing demand for efficient collaboration in DevOps. Docker is a widely used container technology that's become a standard in software development, leading the shift away from full-stack virtualization.

Because these technologies are becoming more important, we want to study their current usage, understand how people create and deploy Docker-based systems, and find better ways to address challenges. While there are many ancillary tools for infrastructure development, very few empirical studies show how they actually improve the development process.

**This presentation shows insights on what software professionals think about using Docker and helps find new ideas for solving current problems.**

## 2. Related Work
There are not many studies that look into the activities involved in creating container and orchestration specifications. Still, we are going to review relevant findings from existing research.

* A study by Guerriero et al. identified conflicting best and bad practices in IaC specifications, noting that available tools lack support for quality-focused maintenance and evolution. The main challenges also primarily revolve around testability and understandability.

* A study conducted by Haque et al. collected data from Stack Overflow and found that most of the Docker questions asked by developers fit into the categories of application development, configuration, networking, basic concepts and debugging.

* Cito et al. evaluated 560 open-source projects on GitHub and found that over a third of Dockerfiles couldn't be built error-free, and many had quality issues. This indicates that errors and quality concerns are frequent in Dockerfile development.

* A study by Rahman et al. showed that approximately half the IaC specifications in 2K IaC scripts contained some kind of syntax and configuration-related defect at one of their revisions, suggesting that this kind of defect may be more common in IaC than in non-IaC solutions. 

* A study by Ibrahim concluded that more than a quarter of the projects analyzed needlessly used Docker-Compose, since they used one single component. They also found that the remaining multi-component specifications mostly use only the basic features of Docker-Compose.

* Some other works identify some opportunities for improving the efficiency of developing Docker specifications and for tools able to reduce the time spent in their development.

Many studies actually overlook technical aspects of container development, such as key activities, challenges, developer practices, and no studies focus on the most time-consuming tasks. Thus, significant limitations exist in maintaining and improving IaC specifications.

## 3. Goals of the Study

We hypothesize that the workflow of a developer configuring a Docker environment is often winding and based on trial-and-error, and that there is a need to study and improve these development activities.

This study answers three research questions in the context of working with Dockerfiles and docker-compose.yml files. 

1. **Which activities are regarded as time-consuming?** <br>
By looking for these, we're searching for areas where developers can work more efficiently and identifying where we need better tools and methods.

2. **Which approaches are used to diagnose and correct problems?** <br>
Finding how people currently deal with problems can help us understand how to support them better or suggest new solutions.

3. **What role is played by ancillary software tools?** <br>
Ancillary tools are extra tools used alongside Docker and Docker-Compose. We hope that finding these tools will show us what developers need most when creating specifications for these platforms and where there might be gaps in the default support they offer.

## 4. Methodology

### Sampling
For the sampling methods, they used **convenience sampling**, a method that involves selecting individuals from the population that are accessible, and they also relied on **referral-chain sampling**, which is when one shares the questionnaire with their colleagues or surroundings.

To prevent oversampling specific subpopulation, the researchers decided to advertise questionnaire through varied experiences and contexts, that is: in **communities gathering** like Slack, Discord, Reddit; **Social networking** like LinkedIn, Twitter, Facebook; and also to **participants of the XP conference** which is the International Conference on Agile Software Development.

To persuade the participation in the survey, they offered the potential respondents **first-hand access to the results**, as well as showed a **short promotional video** that explained the goals of the study and the importance of participating.

### Questionnaire
In terms of the questionnaire, they made in available as an **online form**, where the response time was below 5 mins. They made sure to have precise and targeted questions including **mostly close-ended questions** and some open-ended ones to **identify issues and approaches** that might not have been anticipated in the close-ended questions. The first questions were to understand the participant’s background while the next questions were focused on either Dockerfiles or docker-compose.yml files. They only considered the respondents who reported having some experience creating or modifying those kind of files. As a result, they received **120 responses**.

## 5. Analysis of the Results

### Preliminary Run

Before sending the questionnaire to the sample, the researchers decided to have a preliminary run aiming to validate their questionnaire. They sent the questionnaire to 68 students and 2 researchers. The results show that the students perceive they spend much time understanding why a Docker container is not running as intended (54%) and that few participants (4.4%) use ancillary tools when working with Docker-Compose. Only 1.7% reported confusion of the questionnaire, indicating the researchers can proceed with submitting the questionnaire to the public.

### Demographics

The study gathered data from 120 participants, having diverse contexts and degrees of experience:
* Participants are from 24 different countries.
* Most work in the industry (90%), and some work in academia (12%).
* Most have responsibilities as software developers (87%) and many in operations (54%).

All participants have some years of experience with Docker technologies, working on projects that use these technologies, using these technologies directly (either using Dockerfile or docker-compose.yml files) or creating and updating such files.

The study considers two groups, **the experienced** and **the inexperienced** groups, on one hand having more than 3 years of experience, and on the other hand having less than 3.

### RQ1 — Which Activities are Time Consuming?

Researchers looked into both 1) dockerfile and 2) docker-compose.yml development processes and broke each down into several development activities. In both cases, researchers asked respondents about their attitude towards a considerable amount of time spent in each of these activities. They also looked into how responses may be affected by development experience.

#### Dockerfile Development Process

* A1 Reading Docker documentation.
* A2 Finding out what are the right Dockerfile Commands That I need.
* A3 Finding out what parent image is the most suitable.
* A4 Finding Out What Are The Dependencies My System That must be added to the docker image.
* A5 Confirming if the resulting container is working as intended.
* A6 Trying to understand why the resulting container is not working as intended.
* A7 Finding out which commands are responsible for the container misbehavior.
* A8 Rebuilding the image and re-running the container to confirm that it is working as intended

From this list of activities that were examined, it was found that developers tend to perceive as time-consuming most activities, especially **A4, A5, A6** and **A8**, the last 3 having to do with debugging. They also find that activities are perceived as less time consuming with experience, suggesting developers become more efficient as they progress through the learning curve of Dockerfile development. However, **A4, A5** and **A8** are regarded as time-consuming regardless of the years of experience. 

Researchers suggest more focus should be put into improving activities **A4, A5, A6** and **A8** since they are perceived as the most time consuming globally.

#### Docker-Compose Development Process

* W1 Reading Docker documentation;
* W2 Finding out what are the keys that I need;
* W3 Finding out what images are available;
* W4 Trying to understand why the services are not working as intended;
* W5 (Re)starting the services to confirm that they are working as intended;
* W6 Configuring the properties of each service (e.g., port mapping, name, . . . );
* W7 Configuring the dependencies between the services(e.g., depends_on);
* W8 Configuring volumes and how they are attached to the services;
* W9 Configuring networks and how they are connected to the services;
* W10 Configuring configs and how they are accessed by the services;
* W11 Configuring secrets and how they are accessed by the services. 

Additionally, we have considered the following activities as concerning the reading of Docker-Compose specifications:
* R1 Trying to understand what the services are;
* R2 Trying to understand the dependencies between services (e.g., depends_on);
* R3 Trying to understand what volumes are used and how they are attached to the services;
* R4 Trying to understand what networks are used and how they are connected to the services.

Results show that most activities seem to become easier with experience: activities are only perceived as time consuming by inexperienced developers.  In particular, they consider the following activities as time consuming: configuring properties related to services (W6), and activities related to debugging (W4 and W5) and to documentation (W1 and W2).

**Researchers conclude the following:** Inexperienced users would benefit most from improvements in this area. This is consistent with the view that developers with less experience tend to use a trial-and-error method when debugging.

### RQ2 — Which Approaches are Used to Diagnose and Correct Problems?

Researchers asked what steps or strategies are being followed by respondents to diagnose and fix bugs in the creation of Dockerfiles and docker-compose.yml files. Surprisingly, both experienced and inexperienced developers have similar approaches

The approaches mentioned for problem solving in **Dockerfiles** include:
* trial-and-error
* searching Web resources
* entering the container to execute commands which may help to diagnose the issue manually 
* continuous integration pipelines and
* end-to-end testing

For **Docker-Compose**, the results are similar:
* analysis of the output logs
* execution of commands within the running containers
* isolating services individually, making sure they work as expected
* testing their dependencies

What all these approaches have in common is that they imply leaving the environment where the specification is being written. The process could gain efficiency by introducing approaches that allow to gather feedback within the same environment.

### RQ3 — What Role is Played by Ancillary Software Tools?

In order to answer this research question, researchers asked participants if they use any plugins or tools other than a general-purpose IDE to develop Dockerfiles and docker-compose.yml files. 

The results show that **tools are not widely used**, both by experienced and inexperienced users. Considering activities related to Dockerfile and Docker-Compose development are perceived as time consuming, the paper suggests there is a need for tools that improve the process of writing specifications, beyond what is possible with static analysis alone.

## 6. Threats and Validity and Limitations

There were many efforts to mitigate and identify threats to validity and limitations. They can be divided into 6 categories. 

1. **Questionnaire design<br>**
Online questionnaires primarily used closed-ended questions, potentially limiting result explanations. However, the use of open-ended questions allowed researchers to capture more detailed responses.

2. **Clarity of the questionnaire<br>**
The questionnaire was designed for clarity and precision, but some participants may still interpret questions differently. Initial testing with students and researchers helped address this issue, with only 1.7% reporting confusion. The percentage is low enough to be dismissed.

3. **Honesty of the respondents<br>** Researchers cannot guarantee that the participants answered the questionnaire in a truthful way. However, they believed that the participants had no incentive to give dishonest responses.

4. **Assessment of developer experience** <br> Measuring experience based on years working with Dockerfiles may not be completely reliable since it depends on the participants’ memories as well as more time does not equal more experience. However, consistent and significant correlations in responses provided confidence in the precision of the measurement.

5. **Representativeness of the sample**<br> It is impossible to guarantee that a convenience sample is representative of the entire population. However, the researchers expect the main conclusions of the work to reflect the current state of practice.

6. **Generalization to other IaC platforms** <br>The study focused on Docker and Docker-Compose, limiting the scope of results. Despite this, the researchers believed their findings still hold relevance for a substantial number of professionals.

## 7. Conclusion

In conclusion, the study tries to reach insights on the development of container and orchestration specifications. The focus is on two IaC technologies, Docker and Docker-Compose.

The results were that the Dockerfile development process does present challenging activities and developers tend to perceive most of them as time consuming. The activities that would most benefit from improvements are finding the dependencies and debugging. In terms of Docker-compose, the results were not relevant although the activity that would most benefit from improvement is also debugging. Finally, most developers do not use ancillary tools in their development process.

## 8. Future Research
There are two main key takeaways from this research that can be made into potential future research.

* **Usability evaluation:** participants perform Dockerfile and docker-compose.yml development tasks and are observed to identify the major bottlenecks of the process, using methods such as task analysis or cognitive walkthrough. 

* **New approaches or environments to develop Docker and Docker-Compose specifications:** to address the most time-consuming activities identified in this work and empirically demonstrate their merits and liabilities. Liveness, and live software development may play a relevant role in designing such environments, given their goal of proactively bringing feedback to users or even making the environment automatically act upon this feedback). We also consider that environments that enable visual programming and leverage model-driven engineering techniques can have an important role, especially for developers with less experience.


