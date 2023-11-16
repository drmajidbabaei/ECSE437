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

# Topic#6 \[Taken]

Topic 6: [Container orchestration: A survey](https://link.springer.com/chapter/10.1007/978-3-319-92378-9\_14)



{% hint style="warning" %}
This topic is taken by **Arman Shroff-Mehrabadi!**
{% endhint %}

This presentation was based on the article, “Container Orchestration: A Survey” by Emiliano Casalicchio in 2019.

## Introduction

Modern cloud architectures are increasingly favoring container-centric designs over designs using virtual machines (VMs) across many different use cases. Like VMs, containers solve the “dependency Hell” problem (the issues with having numerous dependencies in large distributed applications), as well as being very portable. Additionally, they are generally faster, less resource-intensive, and easier to manage than VMs, which makes Containers a more popular choice going forward. As such, tools that manage containerized applications (container orchestrators) are more important than ever. 

Container orchestration (using tools such as Kubernetes and Docker Swarm) is developing at breakneck speeds, but there remains many areas in which it can be improved upon. This article discusses the applications and designs of container orchestration technology, monitoring and performance evaluation of these tools, and research-proven features that should be added to orchestration tools. 

## Types of Containers (System, Application, and Container Managers)

Containers are highly efficient because they share the host operating system's kernel, consuming minimal system resources and starting up quickly. This enables rapid scaling of applications, making them ideal for microservices architectures. 
System containers are a specialized type of container technology designed to encapsulate an entire operating system rather than individual applications. They are generally used for managing legacy applications. 
Virtually any new application would be built using application containers, which are the most common and what we have seen in class. They are lightweight, portable, and isolated units of software that encapsulate an application and all its dependencies, making it possible to run software consistently across different environments, from development to production. 
Container managers are frameworks that provide a set of APIs to easily manage the lifecycle (acquire -> build -> deliver -> deploy -> run -> maintain) of a container. Docker is used to manage application containers in a traditional server setup, while cloud providers also offer their own managers to do so on the cloud. 

## Container Orchestration

Container orchestration tools such as Kubernetes or Docker Swarm further enhance scalability and fault tolerance, automating container management in large-scale deployments. Amazon, Microsoft, and other cloud providers also offer tools for container orchestration. Regardless of the flavor of technology used, they all serve the main purpose of enabling selecting, deploying, and dynamically controlling the configuration of multi-container applications. 
Container orchestrators handle numerous tasks, some of which are highlighted below. 

 * Resource limit control allows IT staff to reserve a specific amount of CPU and memory
for a container. These constraints can then be used to make scheduling decisions and to
limit the interference among containers. 

 * Scheduling defines the policy used to place the desired amount of container on desired nodes at a given time instant. Scheduling can be done on the basis
of resource constraints or user configuration. 

* The load balancer does the work of distributing the load among multiple
container instances. Round-robin is the default implemented policy. 

* Fault tolerance can be implemented as replica control and/or a high availability
controller. Replica control allows to specify and maintain a desired number of
containers. A health check, which is achieved by making containers’ TCP, UDP, or SSH  ports open,  is used to determine when a faulty container should be
destroyed and a new one launched to maintain the target number of replicas. 

* Autoscaling enables the automatic adding and removing of containers based on certain policies. This is one of the most important features of container orchestrators. The implemented policies are usually threshold based (by CPU and/or memory usage), but in some cases there are more sophisticated one or the option to define custom
autoscaling policies. 

### Current Limitations 

There is an urgent need of complex adaptation policies to make orchestration a fully automated process with at least the following capabilities: 
Self-healing: to improve the application availability and resiliency
Self-optimization: to balance the tradeoffs between cost and performance while fulfilling Service Level Agreements (SLAs)
Self-protection: to increase system/application security

## Reference Architecture
Casalicchio describes an ideal architecture design, based off of the MAPE_K (Monitor, analyze, plan, execute) self-adaptive cycle that IBM proposed for a self-adaptive auto-recovery system. This system monitors, diagnoses, checks and heals database applications automatically and immediately, without any human intervention. Casalicchio further describes his reference architecture as being multi-layered, in which the container platform layer (where the apps run) and the infrastructure layer (the hosting servers) are coordinated by the adaptation policy. This policy aims to find the optimal configuration, making decisions based on SLA requirements, increases in workload, customer objectives, node health, and other factors. 

## State of the Art Research
There are three areas of container orchestration research Casalicchio highlights: monitoring & analysis and planning, the latter of which includes self-optimization and self-healing.

### Monitoring and Analysis

This section lists numerous studies that measure and analyze the performance of containers versus VMs and other platform technologies for different applications. Some of the studies are concerned with the methodology (and difficulties) in testing the performance of containerized applications. One somewhat thorough study (Felter et. al, 2015) performed a variety of workloads (some were CPU-intensive, network-intensive, or I/O-intensive) and found that by all benchmarks containers outperformed VMs. It should be noted that the difference is often less than 10% and VM technology has been improving relative to container performance. 
Another interesting study (Morabito, 2016) measured the overhead for using containers in IoT devices (which have very constrained processing abilities) and found that, on Raspberry Pi’s at least, the overhead was negligible. 


### Planning

In general, automated container orchestration should be modernized to address the problem of auto-scaling, which is a key component of self-optimization. New automated management solutions should be developed. For instance, it can be difficult to deploy containerized applications across multiple cloud providers, which would be desirable due to rising costs (to the point where it can be cheaper to move away from the public cloud). A study (Abdelbaky et. al., 2015) developed a prototype framework, which would make deploying containers across several different cloud providers (e.g. Azure, AWS, and GCP) simultaneously relatively straightforward. It is not tied to any one provider, nor to a specific orchestration tool so would not only work with Kubernetes. 

Other studies found ways to improve the performance of deployed applications. One study of particular interest (Al-Dhuraibi et. al., 2017) developed “ELASTICDOCKER”, which automatically vertically scales up and down allocated CPU and memory for each container. They found it increased the performance of the deployed application by more than 37% when compared to Kubernetes’ traditional horizontal scaling. Examples such as this reflect the importance of container orchestrators incorporating features proven from more recent research. 

As for self-healing, the author briefly discusses two papers that develop prototypes to enhance the dependability of container orchestration tools. Using computational intelligence (i.e. artificial intelligence), it is possible to predict the possible failure of a managing node on Docker Swarm so that it can be replaced before causing the deployment to crash. 



## Final Remarks

Many of the mechanisms for container orchestration could be improved for runtime self-adaption, with the three areas below being most prescient. 

* Monitoring and Workload Characterization: monitoring techniques and tools used
for the at the OS and application levels do not measure the performance
behavior of containers. Moreover, there is no a commonly agreed definition of QoS
metrics for container-based systems.

* Performance Models: Validated performance models and energy consumption models of container-based systems are inexistent. Performance models are widely
used in autonomic computing to determine the reconfiguration actions needed to
maintain the desired level of service. 

* Adaptation Models for Container Orchestration: As already pointed out, the container orchestration policies used until now are very simple. A framework for QoS-aware, energy-aware, and legislation-aware optimal adaptation models is needed. This framework should allow the user to define system models, QoS, energy, and legal constraints, which it would then use to find optimal adaptation policies for container orchestration at runtime.


## References 

M. Abdelbaky, J. Diaz-Montes, M. Parashar, M. Unuvar and M. Steinder, "Docker Containers across Multiple Clouds and Data Centers," 2015 IEEE/ACM 8th International Conference on Utility and Cloud Computing (UCC), Limassol, Cyprus, 2015, pp. 368-371, doi: 10.1109/UCC.2015.58.

Y. Al-Dhuraibi, F. Paraiso, N. Djarallah and P. Merle, "Autonomic Vertical Elasticity of Docker Containers with ELASTICDOCKER," 2017 IEEE 10th International Conference on Cloud Computing (CLOUD), Honololu, HI, USA, 2017, pp. 472-479, doi: 10.1109/CLOUD.2017.67.

Casalicchio, E. (2019). Container Orchestration: A Survey. In: Puliafito, A., Trivedi, K. (eds) Systems Modeling: Methodologies and Tools. EAI/Springer Innovations in Communication and Computing. Springer, Cham. https://doi.org/10.1007/978-3-319-92378-9_14

R. Morabito, "A performance evaluation of container technologies on Internet of Things devices," 2016 IEEE Conference on Computer Communications Workshops (INFOCOM WKSHPS), San Francisco, CA, USA, 2016, pp. 999-1000, doi: 10.1109/INFCOMW.2016.7562228.

W. Felter, A. Ferreira, R. Rajamony and J. Rubio, "An updated performance comparison of virtual machines and Linux containers," 2015 IEEE International Symposium on Performance Analysis of Systems and Software (ISPASS), Philadelphia, PA, USA, 2015, pp. 171-172, doi: 10.1109/ISPASS.2015.7095802.





