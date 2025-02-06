# What is Kubernetes?  
Kubernetes is an open-source container orchestration platform. It automates the deployment, scaling, and management of containerized applications. Kubernetes can be traced back to Google's internal container orchestration system, Borg, which managed the deployment of thousands of applications within Google. In 2014, Google open-sourced a version of Borg, which is Kubernetes.  

# Why is it called k8s?  
This is a somewhat nerdy way of abbreviating long words. The number 8 in k8s refers to the 8 letters between the first letter “k” and the last letter “s” in the word Kubernetes. Other examples are i18n for internationalization and l10n for localization.  
  
# Kubernetes Architecture  
A Kubernetes cluster is a set of machines, called nodes, that are used to run containerized applications.  

There are two core pieces in a Kubernetes cluster:   
**The Control Plane:** It is responsible for managing the state of the cluster. In production environments, the control plane usually runs on multiple nodes that span across several data center zones.   
**Worker Nodes:** These nodes run the containerized application workloads.    
The containerized applications run in a Pod. Pods are the smallest deployable units in Kubernetes. A pod hosts one or more containers and provides shared storage and networking for those containers.  
Pods are created and managed by the Kubernetes control plane. They are the basic building blocks of Kubernetes applications.  

# Control Plane Components  
The control plane consists of several core components:  
**API Server:** The primary interface between the control plane and the rest of the cluster. It exposes a RESTful API that allows clients to interact with the control plane and submit requests to manage the cluster.  
**etcd:** A distributed key-value store that stores the cluster's persistent state. It is used by the API server and other components of the control plane to store and retrieve information about the cluster.  
**Scheduler:** Responsible for scheduling pods onto the worker nodes in the cluster. It uses information about the resources required by the pods and the available resources on the worker nodes to make placement decisions.  
**Controller Manager:** Responsible for running controllers that manage the state of the cluster. Examples include the replication controller, which ensures that the desired number of replicas of a pod are running, and the deployment controller, which manages the rolling update and rollback of deployments.  

# Worker Node Components  
The core components of Kubernetes that run on the worker nodes include:  
**Kubelet:** A daemon that runs on each worker node. It is responsible for communicating with the control plane, receiving instructions about which pods to run on the node, and ensuring that the desired state of the pods is maintained.  
**Container Runtime:** Runs the containers on the worker nodes. It is responsible for pulling the container images from a registry, starting and stopping the containers, and managing the containers' resources.  
**Kube-proxy:** A network proxy that runs on each worker node. It is responsible for routing traffic to the correct pods and providing load balancing to ensure traffic is distributed evenly across the pods.  

# When to Use Kubernetes?  
As with many things in software engineering, this is all about tradeoffs.  
**Upsides:**  
Scalability and High Availability: Kubernetes is scalable and highly available. It provides features like self-healing, automatic rollbacks, and horizontal scaling, making it easy to scale applications up and down as needed.  
Portability: Kubernetes helps deploy and manage applications consistently and reliably, regardless of the underlying infrastructure. It runs on-premise, in a public cloud, or in a hybrid environment, providing a uniform way to package, deploy, and manage applications.  

**Downsides:**  
Complexity: Kubernetes is complex to set up and operate. The upfront cost is high, especially for organizations new to container orchestration. It requires a high level of expertise and resources to set up and manage a production Kubernetes environment.  
Cost: Kubernetes requires a certain minimum level of resources to run, which can be overkill for many smaller organizations.  

# Managed Kubernetes Services  
One popular option that strikes a reasonable balance is to offload the management of the control plane to a managed Kubernetes service.   
These services are provided by cloud providers like Amazon EKS, GKE on Google Cloud, and AKS on Azure. They allow organizations to run Kubernetes applications without worrying about the underlying infrastructure, handling tasks like setting up and configuring the control plane, scaling the cluster, and providing ongoing maintenance and support.  
  
For mid-size organizations, managed Kubernetes services are a reasonable option to test out Kubernetes. For small organizations, the recommendation is YAGNI - You Ain’t Gonna Need It.  

# What is Helm?  
Helm is a package manager for Kubernetes that allows you to create, share, and use Helm Charts. Using Helm, you can:  
+ Create your own Helm Charts (bundles of YAML files) and push them to a Helm repository for others to use.  
+ Download and use existing Helm Charts from public or private repositories.  
Commonly used deployments like databases (Elasticsearch, MongoDB, MySQL) or monitoring applications (Prometheus) often have complex setups and have pre-made Helm Charts available in repositories. With a simple helm install <chart-name> command, you can reuse configurations that someone else has already created, saving you significant effort. Sometimes, these charts are even created and maintained by the companies that developed the applications.

# Helm break down (Helm Chart) 
Let’s say you have deployed your application in a Kubernetes cluster and now want to deploy Elasticsearch as a new cluster that your application will use to collect its logs.  
To deploy Elasticsearch in your Kubernetes cluster, you will need several components:  
+ StatefulSet: Used for stateful applications like databases.  
+ ConfigMap: For external configuration.  
+ Secret: To store credentials and sensitive data.  
+ ServiceAccount: A user with specific permissions.  
+ Services: To expose the application.  
  
Creating all these files manually by searching for each one separately on the internet can be a tedious and time-consuming task. Since Elastic Stack deployment is pretty standard across clusters, it makes sense that someone has already created these YAML files, packaged them, and made them available for others to use. This bundle of YAML files is called a Helm Chart.  

# Templating Engine  
Another functionality of Helm is Helm Templating Engine, So, what does the Helm templating engine actually mean? Imagine you have an application made up of multiple microservices, and you’re deploying all of them in your Kubernetes cluster. The deployment and service configurations for each microservice are pretty much the same, with the only differences being the application name, version, or Docker image name and version tags.  
  
Without Helm, you would need to write separate YAML configuration files for each microservice. This means you’d have multiple deployment and service files, each with its own application name and version defined. However, since the only differences between these YAML files are a few lines or values, this approach can become repetitive and inefficient.  

**How Helm Simplifies This**
With Helm, you can define a **common blueprint** for all the microservices. The dynamic values (like application name, version, or Docker image) can be replaced with placeholders in a **template file.** This template file is essentially a standard YAML file, but instead of hardcoding values, it uses placeholders that reference external configurations.  
  
For example, a template file might look like this:  
![image](https://github.com/user-attachments/assets/7d0ecec7-469d-4c6d-b3cb-c136ac38ee2c)  

In this template:  
+ {{ .Values.appName }}, {{ .Values.replicas }}, {{ .Values.containerName }}, and {{ .Values.image.repository }}:{{ .Values.image.tag }} are placeholders.  
  
+ These placeholders are replaced with actual values from an external configuration file called values.yaml.  
  
The **values.yaml file** contains the dynamic values that are used in the template. For example:   
![image](https://github.com/user-attachments/assets/f97e699a-9202-4d55-8f9c-2bd8ac73f3b1)

**Dynamic Value Injection**  
You can also override or provide additional values via the command line using the --set flag. For example:  
**helm install my-app --set appName=custom-app --set replicas=5**  

This command dynamically replaces the values in the template with **custom-app** for **appName** and 5 for **replicas**.  

**Benefits of Helm Templating**  
Instead of having multiple YAML files for each microservice, you now have:   
+ One template file that serves as a blueprint for all microservices.  
+ A **values.yaml** file (or command-line overrides) to dynamically inject the specific values for each microservice.  

This approach is especially useful when managing multiple microservices with similar configurations. It reduces redundancy, simplifies maintenance, and makes deployments more efficient.  

# How to manage Kubernetes Clusters and Namespaces  
Managing Kubernetes clusters and namespaces efficiently is crucial for optimizing resources, securing workloads, and maintaining high availability. This guide will cover:  
  
**1. Managing Kubernetes Clusters**  
+ Cluster setup and provisioning  
+ Cluster scaling and resource allocation  
+ Security, authentication, and role-based access control (RBAC)  
+ High availability and resilience  
+ Monitoring and logging  
+ Backup and disaster recovery  
+ Upgrades and maintenance  
+ Managing Namespaces in Kubernetes  
  
**2. Namespace creation and management**  
+ Resource quotas and limits  
+ Role-based access control (RBAC) at the namespace level  
+ Namespace isolation strategies   
+ Namespace monitoring and cleanup strategies  
  
# 1. Managing Kubernetes Clusters  
A Kubernetes cluster consists of multiple nodes that run containerized workloads. Efficient management ensures optimal performance, security, and availability.  
  
**1.1 Cluster Setup and Provisioning**  
There are multiple ways to provision a Kubernetes cluster, depending on whether it's on-premises or cloud-based:  
**On-Premises Deployment:**  
+ Tools: kubeadm, kubespray, or Rancher Kubernetes Engine (RKE)  
+ Requires manual provisioning of control plane and worker nodes  
+ Must configure networking (Calico, Flannel, Cilium)  
+ Hardware provisioning needed for HA clusters  
  
**Cloud-based Deployment:**  
+ Managed Kubernetes Services:  
  + AWS Elastic Kubernetes Service (EKS)  
  + Azure Kubernetes Service (AKS)  
  + Google Kubernetes Engine (GKE)  
  + Oracle Kubernetes Engine (OKE)  
These services handle control plane management, auto-scaling, and security patches  
  
**1.2 Cluster Scaling and Resource Allocation**  
To ensure cluster efficiency, you need proper scaling mechanisms.  
  
Manual Scaling:   
kubectl scale deployment my-app --replicas=5  
  
Horizontal Pod Autoscaler (HPA): Automatically scales pods based on CPU/memory usage  
kubectl autoscale deployment my-app --cpu-percent=50 --min=2 --max=10  

Cluster Autoscaler: Automatically scales worker nodes based on demand. Usually managed by cloud providers  
![image](https://github.com/user-attachments/assets/834006d1-cfd9-416a-aeff-1aaf8a6e6362)  

**1.3 Security, Authentication, and RBAC**  
Security is crucial in Kubernetes cluster management. Key areas include:  
Role-Based Access Control (RBAC): Assigns specific permissions to users or groups  
![image](https://github.com/user-attachments/assets/2842e802-daf9-45cc-8198-a26da78d2c37)  

Network Policies: Restrict inter-pod communication  
![image](https://github.com/user-attachments/assets/5997b3d7-02cc-45f9-ad9c-77fb92caf52e)  
  
Secrets Management: Store sensitive information like API keys and passwords securely  
kubectl create secret generic my-secret --from-literal=password='P@ssw0rd'  

![image](https://github.com/user-attachments/assets/87003a89-caa8-416f-ae27-e802894faa1c)  
![image](https://github.com/user-attachments/assets/b0d97b8d-05c2-43a2-9ff8-46c519961653)  
![image](https://github.com/user-attachments/assets/3930aa87-83fc-4a81-83ae-9df64579cb2e)  
![image](https://github.com/user-attachments/assets/6852fa37-045b-4dfd-b7e0-ed02440189d2)  

# Ingress  
![image](https://github.com/user-attachments/assets/c39fc22c-16eb-4367-91a2-3c2035c5a494)  
![image](https://github.com/user-attachments/assets/bd56afb6-2c2d-4fef-97ae-8ce22e1fa81f)  
![image](https://github.com/user-attachments/assets/f4188ff3-1e47-4620-a438-2e900c49ef46)  
# 4. TLS/SSL Termination  
Ingress can handle HTTPS traffic and terminate SSL using TLS secrets.  
![image](https://github.com/user-attachments/assets/56d12e44-23b0-4c8c-93ee-03df628b6073)  
![image](https://github.com/user-attachments/assets/ef1a2167-1b61-4d01-825a-32cabb137ca1)  

![image](https://github.com/user-attachments/assets/c2d3f2f7-fb9e-4906-ba51-fa82f66eeebb)  
![image](https://github.com/user-attachments/assets/d3efc1d7-afe3-4d4f-85b8-c3d18a10cb75)   

**Conclusion**  
+ Ingress allows external access to Kubernetes services with routing, SSL, and security.  
+ It needs an Ingress Controller to function.  
+ Supports path-based, host-based, and TLS termination.  
+ NGINX Ingress Controller is the most widely used.  


