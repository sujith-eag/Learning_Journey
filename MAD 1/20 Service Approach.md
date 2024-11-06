
SasS, IaaS, PaaS

### Service approach
Instead of one person doing everything, better to specialize.

SaaS - Hosted solutions: all the software is installed and maintained

IaaS - Raw machines, power, networking. Other things is left to user
Cloud compute systems

Platforms 
Combination of specific hardware and software
PaaS
Develper manages the code, specify requirements on server sizing, database, connectivity.
replit, glitch, Google app engine

------
Version control
To retain backups, Develop new features and fix bugs

hotfix branch, release branch, develop branch, feature branches
CI/CD

-------
containers
Self contained environment with OS and minimal Libraries - just enough to run process.
it is not just a virtual machine, its aim is to have less impact on the resources of system.
Primarily used with Linux kernel namespaces which knows where the request is coming from so prevents disturbing other parts of the system.

why?
Full os is impossible to version control, so few minimum requirements are set up which dont have to be upgraded, needs no more libraries. So can create a self-contained images that can be version control.
Sandboxing image cannot affect other processes on system.

How?
Kernel level support needed
All communication is "inter-container" - networking

containers, docker a software allowing to manage the containers

Orchestration
The different processes of the app can be its own container, making it scalable type.
Starting in some specific order (dependencies)
Communicating between processes that are isolated - network.

Mechanisms to build and orchestrate, automate - docker-compose, Kubernetes
Is a key to understanding and managing large scale deployments



________
---

## Cloud Service Models: SaaS, IaaS, and PaaS

### **SaaS (Software as a Service)**  
**Definition**: SaaS is a cloud computing model where software applications are hosted by a provider and made available to users over the internet. These applications are fully managed by the service provider, including maintenance, updates, and infrastructure.

- **Examples**: Google Workspace (Docs, Sheets), Microsoft 365, Salesforce, Dropbox.
- **Key Characteristics**:
  - **Hosted solutions**: The provider takes care of the infrastructure, software installation, and ongoing maintenance.
  - **No user management**: The user doesn't need to worry about hardware, operating systems, or application management.
  - **Scalability**: SaaS solutions are often highly scalable with usage-based pricing.
  - **Accessibility**: Users can access the software via a web browser on various devices, which provides flexibility and mobility.
  
### **IaaS (Infrastructure as a Service)**  
**Definition**: IaaS provides virtualized computing resources over the internet. The user is responsible for managing and configuring the operating systems, applications, and data, while the provider handles the underlying infrastructure, such as servers, storage, and networking.

- **Examples**: Amazon Web Services (AWS), Microsoft Azure, Google Cloud Platform (GCP), DigitalOcean.
- **Key Characteristics**:
  - **Raw infrastructure**: Users rent raw computing power, storage, and networking resources, but they must configure and manage their own virtual machines and applications.
  - **Customization**: Provides high flexibility, allowing users to install custom software and configure environments according to their needs.
  - **Scalability**: Users can scale resources up or down based on demand.
  - **Cost Efficiency**: Pay-as-you-go pricing model can be cost-effective for varying workloads.
  
### **PaaS (Platform as a Service)**  
**Definition**: PaaS provides a platform allowing developers to build, deploy, and manage applications without dealing with the underlying infrastructure. PaaS offers a set of tools and services to assist with development, such as databases, messaging systems, and developer tools.

- **Examples**: Google App Engine, Microsoft Azure App Services, Heroku, Red Hat OpenShift, Replit, Glitch.
- **Key Characteristics**:
  - **Focus on development**: Developers can focus on writing code and defining application requirements, such as server sizes, database specifications, and connectivity.
  - **Integrated services**: PaaS solutions often come with built-in services for databases, security, monitoring, and scalability.
  - **Automation**: Many PaaS platforms offer automated deployment pipelines and scaling features.
  - **Less control**: Compared to IaaS, PaaS offers less customization of the underlying infrastructure but simplifies app development.
  
### **Service Approach to Cloud Models**  
Rather than relying on one person to manage everything in the IT stack, cloud computing promotes specialization:
- **SaaS**: The provider takes care of all software installation, updates, and maintenance.
- **IaaS**: The user manages their own software stack, from the operating system to applications, while the provider ensures the availability of infrastructure.
- **PaaS**: Developers manage their code and application requirements while the platform provider takes care of the infrastructure and other platform-level services.

---

## **Version Control**

Version control is a system that allows developers to track changes in code, revert to previous versions, and collaborate efficiently on software development projects.

### **Key Functions**:
- **Backup retention**: Safeguards the development process by allowing you to revert to previous states.
- **Collaboration**: Multiple developers can work on the same codebase without interfering with each other’s work.
- **Feature development**: Enables the development of new features and simultaneous bug fixes without disrupting the main product.
  
### **Branching Strategies**:
- **Hotfix branch**: A branch used to quickly address and fix critical issues in the live application.
- **Release branch**: Used to prepare code for release, usually for final testing and packaging.
- **Develop branch**: The main branch where new features are developed and integrated.
- **Feature branches**: Branches dedicated to specific features or changes, which are later merged into the develop or master branch.

### **CI/CD (Continuous Integration/Continuous Deployment)**  
- **Continuous Integration (CI)**: A practice where developers frequently integrate their code into a shared repository, which is then automatically tested to detect bugs and integration issues.
- **Continuous Deployment (CD)**: Extends CI by automating the deployment process so that every change that passes automated tests is automatically pushed to production.

---

## **Containers and Virtualization**

Containers are a lightweight form of virtualization that packages an application and its dependencies into a single unit. Containers allow applications to run consistently across different environments.

### **What Are Containers?**  
- **Self-contained environment**: Containers include everything the application needs to run—such as the code, runtime, system tools, and libraries—without the need for a full operating system.
- **Efficiency**: Containers are more resource-efficient compared to full virtual machines because they don’t require the overhead of a separate OS for each instance.
- **Portability**: Containers can be run across different environments (development, staging, production) without modification.
  
### **Why Use Containers?**
- **Version control**: Traditional virtual machines cannot be easily versioned because they include full OS installations. Containers only package necessary components, making it easier to manage versions.
- **Resource efficiency**: Containers share the host OS kernel, resulting in less overhead compared to VMs.
- **Isolation and security**: Containers are isolated from one another, reducing the risk of one process affecting others on the same host.
- **Consistency**: Ensures that applications run the same way in any environment.

### **How Do Containers Work?**
- **Kernel-level support**: Containers rely on features like Linux kernel namespaces and control groups to isolate processes, manage resources, and prevent interference between containers.
- **Inter-container communication**: Containers can communicate with each other over a network, enabling complex multi-container applications (e.g., microservices) to function together.

### **Popular Containerization Tools**:
- **Docker**: Docker is a platform that enables the creation, deployment, and management of containers. It provides tools for building, packaging, and running containers.
- **Docker Compose**: A tool for defining and running multi-container Docker applications, simplifying orchestration and service management.
  
---

## **Container Orchestration**

As applications scale, managing individual containers becomes more complex. **Container orchestration** tools are designed to automate the deployment, scaling, and management of containerized applications.

### **Key Orchestration Tools**:
- **Kubernetes**: An open-source container orchestration platform that automates deployment, scaling, and operations of application containers. Kubernetes enables high-availability, load balancing, and management of containerized services.
- **Docker Swarm**: Docker's native orchestration tool for clustering and managing a group of Docker hosts, providing load balancing, service discovery, and scaling.
  
### **Orchestration in Action**:
- **Scaling**: Containers can be scaled up or down based on demand. Orchestration tools help in automatically provisioning new containers and deallocating resources as needed.
- **Dependencies**: Orchestrators ensure that containers start in the correct order based on their dependencies (e.g., databases must be running before web servers).
- **Network management**: Containers may need to communicate with each other, and orchestration tools handle networking between containers, ensuring secure communication.

### **Why Orchestration Is Essential**:
- **Automation**: Orchestration automates complex tasks such as container deployment, scaling, and management.
- **Consistency**: Ensures the environment is consistent and can be replicated across multiple instances.
- **Fault tolerance**: Automatically replaces failed containers and manages failovers, ensuring high availability.

---

## **Conclusion**

The cloud service models (SaaS, IaaS, and PaaS) cater to different levels of abstraction, from fully managed services (SaaS) to infrastructure-level control (IaaS) to developer-focused platforms (PaaS). The rise of containers and orchestration tools like Kubernetes and Docker has revolutionized how developers deploy, manage, and scale applications. These technologies enable greater efficiency, flexibility, and reliability in modern cloud-based applications.




