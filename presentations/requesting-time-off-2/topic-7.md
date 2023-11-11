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

# Topic#7 \[Taken]

Topic 7: [Machine learning-based orchestration of containers: A taxonomy and future directions](https://dl.acm.org/doi/abs/10.1145/3510415)

{% hint style="warning" %}
This topic is taken by Hadi **Ghaddar and Omar Marwan!**
{% endhint %}

This presentation was inspired by the paper Machine Learning-based Orchestration of Containers: A Taxonomy and Future Directions, published on September 13 2022 and authored by Zhiheng Zhong, Minxian Xu, Maria Alejandra Rodriguez, Chengzhong Xu and Rajkumar Buyya.

## Introduction ##

In the past decade, cloud computing has gained popularity for its efficiency and scalability. Leading cloud services like AWS, Google Cloud, and Azure, initially relying on Virtual Machines (VMs), have transitioned to containers. Unlike VMs, containers don't need a separate operating system, making them more lightweight and efficient. This shift has prompted companies to favor containerization over VMs, leading to the rise of container orchestration techniques for managing cloud-based applications.

Container orchestration automates the lifecycle of containers, including the deployment, management, and scaling of containers without worrying about the underlying infrastructure. This proves advantageous for cloud providers handling numerous containers simultaneously, improving resource utilization and application performance. However, as the demand for cloud workloads grows, container orchestration techniques need to be enhanced to meet future expectations.

To meet these demands, companies are turning to Machine Learning (ML) techniques. ML algorithms help create complex models that understand and predict application metrics like resource utilization. This enables more accurate and efficient resource provisioning decisions, optimizing workloads in the ever-evolving cloud computing landscape.

## Background ##

Containers have a history that traces back to the 1970s, with roots in technologies like chroot Unix operation, which was the first glimpse into process isolation. However, their widespread adoption began in the 2010s with the introduction of Docker, and they have been rising in popularity ever since. 

- Containers are lightweight packages of application code bundled together with dependencies such as specific versions of programming language runtimes and libraries required to run software services.
- Containerization provides a clear separation of responsibility, as developers focus on application logic and dependencies, while IT operations teams can focus on deployment and management instead of application details such as specific software versions and configurations.
- Containers can also run virtually anywhere, greatly easing development and deployment.
- Containers virtualize CPU, memory, storage, and network resources at the operating system level, providing developers with a view of the OS logically isolated from other applications.

As application architectures become more complex and the number of containers needed to maintain stability across a distributed system grows, companies, such as cloud service provides, can simplify the management of their container infrastructure with container orchestration. 

- Container orchestration empowers cloud service providers by allowing them to capture the benefits of containerization at scale without incurring additional maintenance overhead by automating the complete lifecycle of containers, including configuration, deployment, and scaling
- Container orchestration simplifies operations through automated container management, can automatically restart or scale a container or group of containers, and add security by reducing the chance of human error.

An example of a leading orchestration tool is the widely used Kubernetes, which is an open-source platform developed by Google that helps companies build and manage containerized applications across multiple hosts, dynamically deploying, scheduling, and scaling them. 

For future needs (and even some upcoming), current orchestration techniques are simply not equipped to deal with them, and enhancements to these techniques will be required to keep up with industry & customer expectations.

Machine learning is a method of data analysis that automates analytical model building. It is a branch of artificial intelligence based on the idea that systems can learn from data, identify patterns, and make decisions with minimal human intervention. Machine Learning presents the following benefits:
- It can handle and process large amounts of data.
- It has improved accuracy & efficiency over standard methods through training.
- It requires little to no human interaction.
- It can form accurate predictions on data through pattern recognition.
- It can be applied in all facets of software delivery.

Machine learning can be leveraged to perform complex calculations to predict trends, and we can use this in tandem with container orchestration ; through a machine learning-based Optimization Engine, we can build ML models based on analysis of monitoring data and system logs received from the orchestrator. Furthermore, it can produce future resource provisioning decisions relying on the generated behavior models and prediction results. 

## Machine Learning Based Container Orchestration Techniques ##

Containerized applications can be composed through three different types of architecture: 
| Architecture | Description | 
| ------------ | ----------- |
| Monolithic | Monolithic applications follow an all-in-one architecture where all the functional modules are developed and configured into exactly one deployment unit, namely, one container. However, it is hard and impractical to scale these applications to higher complexities as testing and development becomes resource intensive, thus making the architecture exclusively suitable for small-scale applications with simple internal structures. |
| Microservice | Microservice applications break down a complex application into multiple loosely coupled components called microservices. Each microservice unit can be deployed and operated independently for different functionalities and business objectives, and they can interact with each other. With each microservice unit, a new container must be implemented and maintained, which can cause system resources to plummet if not well managed. |
| Serverless | Serverless applications allow developers to build and run services without having to manage the underlying infrastructure. Developers can write and deploy code, while a cloud provider provisions servers to run their applications, databases, and storage systems at any scale. However, when a function hasn’t been used for a while, it is killed. This means that when it is called again, the time it takes the code to run is temporarily slowed, also known as a cold start, which could affect performance. |

Machine Learning can thus help us leverage efficient solutions depending on the architecture used by our workload. Within these workloads, ML can enhance various aspects of the application and infrastructure through multiple means:
-	Time series analysis can be used to predict request arrival rates and resource usage patterns, allowing us to predict when and how many new containers should be provisioned or terminated, which can help optimize resource allocation. This analysis also allows our Machine Learning engine to dynamically allocate resources to containers based on real time demand and metrics. This ensures that resources are efficiently used and distributed effectively to allow applications to run smoothly. 
-	Anomaly detection is a critical mechanism for identifying abnormal behaviors in system states or application performance, and ML algorithms can utilize this by monitoring the behavior of containers, since cloud computing is subject to security attacks and threats. Through the identification of critical performance indicators that support anomaly detection, including network activity and CPU utilization, companies can identify security breaches instantaneously at any time.
-	Load balancing between microservices under the multi-cloud environment could be rather complex, because of the unstable network latency, dynamic service configuration, and fluctuating application workloads. To address this challenge, ML can produce optimal request chains for each microservice unit to ensure proper queueing and resource management, dynamically updating the requests chains in case of environmental changes.
-	Task scheduling is an issue in all OS based systems, and ML can help us alleviate these issues, as we can use approximation algorithms such as best fit to make scheduling decisions with improved resource utilization and energy efficiency. 
-	ML can predict when containers or infrastructure components are likely to fail or require maintenance. This can help orchestration platforms schedule proactive maintenance or failover procedures, minimizing downtime in cloud computing software solutions.

## Conclusion ##

Cloud Computing has revolutionized software delivery, offering cost-effective and scalable solutions to deploy and manage solutions. Cloud service providers have made the switch from Virtual Machines to Containers, which package applications and their dependencies, making them lightweight, efficient, and highly portable without maintaining an OS. In consequence, orchestration techniques have emerged as the preferred method for managing containerized applications, automating deployment, scaling, and maintainability. As the demand for bigger and better cloud workloads continues to surge, container orchestration must evolve to meet these standards, which can be possible with Machine Learning.

Through Machine Learning’s use of data and algorithms to make predictions and recognize patterns, we can integrate Machine Learning based optimization engines into orchestration to create models that can predict and optimize resource allocation and provisioning.  ML-based models could produce more accurate orchestration decisions with shorter computation delays, under complex and dynamic cloud environments consisting of geographically distributed computation resources.

ML-based orchestration approaches and will also help to select the most suitable techniques for efficient container orchestration with the specific requirement under different application architectures, such as microservices and serverless architectures to handle the sustainably growing system complexity and balance multi-dimensional optimization objectives.

Through this synergy, companies will be able to create more scaled and robust cloud computing services which will help benefits users and businesses alike, opening a new frontier for new potential ways of accessing services through the web. 

## References ## 

Zhong, Z., Xu, M., Rodriguez, M. A., Xu, C., &amp; Buyya, R. (2022, January 1). Machine learning-based orchestration of containers: A taxonomy and Future Directions. ACM Digital Library.

Google. What is container orchestration? Google, https://cloud.google.com/discover/what-is-container-orchestration#:~:text=Container%20orchestration%20automatically%20provisions%2C%20deploys,life%20cycle%20management%20of%20containers. 

Docker. What is a Container? Docker, https://www.docker.com/resources/what-container/

IBM. What is Machine Learning? IBM, https://www.ibm.com/topics/machine-learning
