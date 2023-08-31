# kubernetes-getting-started

 Kubernetes is a powerful container orchestration platform used to manage and deploy containerized applications. Here's a step-by-step guide to help you learn Kubernetes from scratch:

Step 1: Understanding the Basics

    Containerization Concepts: Before diving into Kubernetes, make sure you have a good understanding of containerization. Learn about Docker, as it's a popular containerization tool that works seamlessly with Kubernetes.

    Basic Linux Skills: Since you're using Ubuntu, familiarize yourself with basic Linux command-line operations. This knowledge will be crucial when interacting with Kubernetes.

Step 2: Set Up Your Learning Environment

    Install Docker: You'll need Docker to create and manage containers. Install Docker on your Ubuntu machine and practice creating and running containers.

    Install Minikube: Minikube is a tool that lets you run a single-node Kubernetes cluster locally for development and learning purposes. Install Minikube to get a hands-on experience with Kubernetes without dealing with cloud services initially.

Step 3: Core Kubernetes Concepts

    Pods: Pods are the smallest deployable units in Kubernetes. They can contain one or more containers. Learn how to create pods and interact with them.

    Deployments: Deployments manage the lifecycle of pods. They provide features like scaling, rolling updates, and rollbacks. Understand how to create and manage deployments.

    Services: Services provide networking and load balancing for your pods. Learn about different types of services and how to expose your applications.

    ReplicaSets: While deployments manage pods, they use ReplicaSets under the hood. Understanding ReplicaSets will give you insights into how scaling and rolling updates work.

Step 4: Advanced Concepts

    Namespaces: Namespaces help you logically isolate resources within a cluster. Learn how to create and manage namespaces.

    ConfigMaps and Secrets: These are used to manage configuration and sensitive data separately from your application code.

    Persistent Volumes and Persistent Volume Claims: Understand how Kubernetes manages storage for your applications that require persistence.

    Ingress: Ingress controllers allow you to route external traffic to your services. Learn how to set up and manage Ingress resources.

Step 5: Kubernetes Ecosystem Tools

    kubectl: The command-line tool used to interact with Kubernetes clusters. Learn its commands and options.

    Helm: Helm is a package manager for Kubernetes. It helps you define, install, and manage Kubernetes applications.

    Kubernetes Dashboard: Install the Kubernetes Dashboard to get a graphical interface for managing your cluster.

Step 6: Real-world Scenarios

    Create Your Own Application: Deploy a simple application with multiple services, replicas, and persistent storage. This will help you apply what you've learned in a practical context.

    Practice Scaling and Updates: Experiment with scaling your application up and down, and perform rolling updates to see how Kubernetes handles these scenarios.

    Monitoring and Logging: Explore tools like Prometheus for monitoring and tools like Fluentd or Loki for logging in a Kubernetes environment.

Step 7: Further Learning

    Online Courses and Tutorials: There are many online resources and courses that provide in-depth knowledge of Kubernetes. Platforms like Kubernetes official website, Udemy, Coursera, and edX offer great courses.

    Read Documentation: The Kubernetes official documentation is an invaluable resource. It's comprehensive and regularly updated.

    Join the Community: Engage with the Kubernetes community through forums, blogs, and social media. Learning from others' experiences can be very beneficial.

Remember that Kubernetes is a complex system, and it's okay to take your time to fully grasp its concepts. Practice and hands-on experience are key to becoming proficient. Good luck on your Kubernetes learning journey!


control plane : responsible for kubernets function

KUbernets worker nodes: nodes can be vitural or phy
managed by contorl plane


kubelet: gets pod specifications from the kubernets api. ensures that pods are running healthy, 

controller: gets the desired state 

kuberneatees proxy: has network rules , network proxy

kubernets objects: persistent entities  eg: pods,namespaces, deployment, volumes. we use kubernaties api towrok with them(kubectl)
namespaces and name: name spaces are used for virtualization of physical cluster to segregate cluster by team, proj etc.

Kubernets objects:
pod: represents proccess running in clustter, its a simplest unit in kerbernets
we can replecate pod services to scalee the application horizontaly

replica set: set of identical pods 
deployments: provides updates for pods and replica sets

Kubectl CLI:
ex: kubectl run nginx --image ngnix

running with yaml file:
ex: kubectl create -f nginx.yaml

Summary & Highlights

Congratulations! You have completed this module. At this point, you know: 

    Container orchestration automates the container lifecycle resulting in faster deployments, reduced errors, higher availability, and more robust security. 

    Kubernetes Is a highly portable, horizontally scalable, open-source container orchestration system with automated deployment and simplified management capabilities.  

    Kubernetes architecture consists of a control plane and one or more worker planes. 

    A control plane includes controllers, an API server, a scheduler, and an etcd. 

    A worker plane includes nodes, a kubelet, container runtime, and kube-proxy. 

    Kubernetes objects include Namespaces, Pods, ReplicaSets, Deployments, and Services. 

    Namespaces help in isolating groups of resources within a single cluster. 

    Pods represent a process or an instance of an app running in the cluster. 

    ReplicaSets create and manage horizontally scaled running Pods. 

    Deployments provide updates for Pods and ReplicaSets. 

    A service in Kubernetes is a REST object that provides policies for accessing the pods and cluster. 

    Kubernetes capabilities include automated rollouts and rollbacks, storage orchestration, horizontal scaling, automated bin packing, secret and configuration management, Ipv4/Ipv6 dual-stack support, batch execution, self-healing, service discovery, load balancing, and extensible design. 

    Services in Kubernetes are REST objects that provide policies for accessing the pods and cluster. ClusterIP provides Inter-service communication within the cluster; a NodePort Service creates and routes the incoming requests automatically to the ClusterIP Service; the External Load Balancer, or ELB, creates NodePort and ClusterIP Services automatically and External Name service represents external storage as well as enables Pods from different namespaces to talk to each other.

    Ingress is an API object that provides routing rules to manage external users' access to multiple services in a Kubernetes cluster; whereas using a DaemonSet ensures that there is at least one copy of the pod on all nodes; a StatefulSet manages stateful applications, manages Pod deployment and scaling, maintains a sticky identity for each Pod request and provides persistent storage volumes for your workloads and lastly a Job creates pods and tracks the Pod completion process; Jobs are retried until completed.  


 Glossary: Kubernetes Basics

Term	Definition
Automated bin packing 	Increases resource utilization and cost savings using a mix of critical and best-effort workloads.
Batch execution 	Manages batch and continuous integration workloads and automatically replaces failed containers, if configured.
Cloud Controller Manager 	A Kubernetes control plane component that embeds cloud-specific control logic. The cloud controller manager lets you link your cluster into your cloud provider's API, and separates out the components that interact with that cloud platform from components that only interact with your cluster.
Cluster 	A set of worker machines, called nodes, that run containerized applications. Every cluster has at least one worker node.
Container Orchestration 	Container orchestration is a process that automates the container lifecycle of containerized applications.
Container Runtime 	The container runtime is the software that is responsible for running containers.
Control Loop 	A non-terminating loop that regulates the state of a system. A thermostat is an example of a control loop.
Control plane 	The container orchestration layer that exposes the API and interfaces to define, deploy, and manage the lifecycle of containers.
Controller 	In Kubernetes, controllers are control loops that watch the state of your cluster, then make or request changes where needed. Each controller tries to move the current cluster state closer to the desired state.
Data (Worker) Plane 	The layer that provides capacity such as CPU, memory, network, and storage so that the containers can run and connect to a network.
DaemonSet 	Ensures a copy of a Pod is running across a set of nodes in a cluster.
Declarative Management 	A desired state that can be expressed (for example, the number of replicas of a specific application),and Kubernetes will actively work to ensure that the observed state matches the desired state.
Deployment 	An object that provides updates for both Pods and ReplicaSets. Deployments run multiple replicas of an application by creating ReplicaSets and offering additional management capabilities on top of those ReplicaSets. In addition, deployments are suitable for stateless applications.
Designed for extensibility 	Adds features to your cluster without adding or modifying source code.
Docker Swarm 	automates the deployment of containerized applications but was designed specifically to work with Docker Engine and other Docker tools making it a popular choice for teams already working in Docker environments.
Ecosystem 	A composition of services, support and tools that are widely available. The Kubernetes ecosystem is a large, rapidly growing ecosystem where its services, support, and tools are widely available.
etcd 	A highly available key value store that contains all the cluster data. For any deployment, the deployment configuration is stored in etcd. It is the source of truth for the state in a Kubernetes cluster, and the system works to bring the cluster state into line with what is stored in etcd.
Eviction 	Process of terminating one or more Pods on Nodes.
Imperative commands 	Create, update, and delete live objects directly.
Imperative Management 	Defining steps and actions to get to a desired state.
Ingress 	An API object that manages external access to the services in a cluster, typically HTTP.
IPv4/IPv6 dual stack 	Assigns both IPv4 and IPv6 addresses to Pods and Services.
Job 	A finite or batch task that runs to completion.
Kubectl 	Also known as kubectl Command line tool for communicating with a Kubernetes cluster's control plane, using the Kubernetes API.
Kubelet 	The kubelet is the primary "node agent" that runs on each node. The kubelet takes a set of PodSpecs (a YAML or JSON object that describes a pod) provided primarily through the apiserver and ensures that the containers described in those PodSpecs are running and healthy. The kubelet doesn't manage containers which were not created by Kubernetes.
Kubernetes 	is the de facto open-source platform standard for container orchestration. It was developed by Google and is maintained by the Cloud Native Computing Foundation (CNCF). Kubernetes automates container management tasks, like deployment, storage provisioning, load balancing and scaling, service discovery, and fixing failed containers. Its open-source toolset and wide array of functionalities are very attractive to leading cloud providers, who both support it, and in some cases, also offer fully managed Kubernetes services.
Kubernetes API 	The application that serves Kubernetes functionality through a RESTful interface and stores the state of the cluster.
Kubernetes API Server 	The Kubernetes API server validates and configures data for the api objects which include pods, services, replication controllers, and others. The API Server services REST operations and provides the frontend to the cluster's shared state through which all other components interact.
Kubernetes Controller Manager 	Runs all the controller processes that monitor the cluster state and ensures that the actual state of a cluster matches the desired state. Examples of controllers that ship with Kubernetes are the replication controller, endpoints controller, namespace controller, and service accounts controller.
Kubernetes Cloud Controller Manager 	A Kubernetes control plane component that embeds cloud-specific control logic. The cloud controller manager lets you link your cluster into your cloud provider's API, and separates out the components that interact with that cloud platform from components that only interact with your cluster.
Kubernetes Proxy 	A network proxy that runs on each node in a cluster. This proxy maintains network rules that allow communication to Pods running on nodes—in other words, communication to workloads running on the cluster. The user must create a service with the apiserver API to configure the proxy.
kube-scheduler 	Control plane component that watches for newly created Pods with no assigned node, and selects a node for them to run on.
Label Selector 	Allows users to filter a list of resources based on labels.
Labels 	Tags objects with identifying attributes that are meaningful and relevant to users.
Load balancing 	Balances traffic across Pods for better performance and high availability.
Marathon 	is an Apache Mesos framework. Apache Mesos is an open-source cluster manager developed by UC Berkeley. It lets users scale container infrastructure through the automaton of most management and monitoring tasks.
Namespace 	An abstraction used by Kubernetes to support isolation of groups of resources within a single cluster.
Node 	The worker machine in a Kubernetes cluster. User applications are run on nodes. Nodes can be virtual or physical machines. Each node is managed by the control plane and is able to run Pods.
Nomad 	(Hashicorp) is a free and open-source cluster management and scheduling tool that supports Docker and other applications on all major operating systems across all infrastructure, whether on-premises or in the cloud. This flexibility lets teams work with any type and level of workload.
Object 	An entity in the Kubernetes system. The Kubernetes API uses these entities to represent the state of your cluster.
Persistence 	Ensures that an object exists in the system, until the object is modified or removed.
Preemption 	Logic in Kubernetes helps a pending Pod to find a suitable Node by evicting low priority Pods existing on that Node.
Self-healing 	Restarts, replaces, reschedules, and kills failing or unresponsive containers.
Service 	An abstract way to expose an application running on a set of Pods as a network service.
Service Discovery 	Discovers Pods using their IP addresses or a single DNS name.
StatefulSet 	Manages the deployment and scaling of a set of Pods, and provides guarantees about the ordering and uniqueness of these Pods.
Storage 	A data store that supports persistent and temporary storage for Pods.
Storage Orchestration 	Automatically mounts your chosen storage system whether from local storage, network storage, or public cloud.
Pod 	The smallest and simplest Kubernetes object. Represents a process running in a cluster; it also represents a single instance of an application running in a cluster. Usually, a Pod wraps a single container but, in some cases encapsulates multiple tightly coupled containers that share resources.


Deployment Strategies
Overview

A Kubernetes deployment strategy defines an application’s lifecycle that achieves and maintains the configured state for objects and applications in an automated manner. Effective deployment strategies minimize risk.

Kubernetes deployment strategies are used to: 

    Deploy, update, or rollback ReplicaSets, Pods, Services, and Applications 

    Pause/Resume Deployments 

    Scale Deployments manually or automatically 

Types of deployment strategies

The following are six types of deployment strategies:

    Recreate 

    Rolling 

    Blue/green 

    Canary 

    A/B testing 

    Shadow 

You can use either a single deployment strategy or a combination of multiple deployment strategies.
Recreate strategy 

In the recreate strategy, Pods running the live version of the application are all shut down simultaneously, and a new version of the application is deployed on newly created Pods. 

Recreate is the simplest deployment strategy. There is a short downtime between the shutdown of the existing deployment and the new deployment. 

Recreate strategy steps include:

    A new version of the application (v2) is ready for deployment. 

    All Pods running the current version (v1) are shut down or deleted. 

    New (v2) Pods are created. 

The rollback process is completed in the reverse order, replacing version 2 (v2) with version 1 (v1).

Pros
	

Cons

Simple setup
	

Short downtime occurs between shutdown and new deployment

Application version completely replaced
	

Rolling (ramped) strategy 

In a rolling strategy, each Pod is updated one at a time. A single v1 Pod is replaced with a new v2 Pod. Each v1 Pod is updated in this way until all Pods are v2. During a rolling strategy update, there is hardly any downtime since users are directed to either version.

Rolling strategy steps include:

    A new version of the application (v2) is ready for deployment. 

    One of the Pods running the current version (v1) is shut down or deleted. 

    A new (v2) Pod is created to replace the (v1) Pod that was removed. 

    Steps 2 and 3 are repeated until all (v1) Pods are removed and replaced with (v2) Pods. 

The rollback process is reversed, where v2 Pods are replaced by v1 Pods. 

Pros
	

Cons

Simple setup
	

Rollout/rollback takes time 

Suitable for stateful applications that need to handle rebalancing of the data
	

You cannot control traffic distribution
Blue/green strategy

In a blue/green strategy, the blue environment is the live version of the application. The green environment is an exact copy that contains the deployment of the new version of the application. The green environment is thoroughly tested. Once all changes, bugs, and issues are addressed, user traffic is switched from the blue environment to the green environment.

Blue/green strategy steps include:

    Create a new environment identical to the current production environment. 

    Design the new version and test it thoroughly until it is ready for production. 

    Route all user traffic to the new version. 

To perform a rollback, switch the environments back.

Pros
	

Cons

Instant rollout/rollback 
(no downtime)
	

Expensive 
(requires double resources)

New version is available immediately to all users
	

Rigorous testing required before releasing to production

	

Handling stateful applications is difficult
Canary strategy

In a canary strategy, the new version of the application is tested using a small set of random users alongside the current live version of the application. Once the new version of the application is successfully tested, it is then rolled out to all users. 

Canary strategy steps include:

    Design a new version of the application. 

    Route a small sample of user requests to the new version. 

    Test for efficiency, performance, bugs, and issues, and rollback as needed. 

    Repeat steps 1 to 3. Once all issues are resolved, route all traffic to the new version.  

Rollback has no downtime since few users are exposed to the new version.

Pros
	

Cons

Convenient for reliability, error, and performance monitoring
	

Slow rollout, gradual user access

Fast rollback
	

A/B testing strategy

The A/B testing strategy, also known as split testing, evaluates two versions of an application (version A and version B). With A/B testing, each version has features that cater to different sets of users. You can select which version is best for global deployment based on user interaction and feedback. 

A/B testing strategy steps include:

    Design a new version of the application by adding mostly UI features. 

    Identify a small set of users based on conditions like weight, cookie value, query parameters, geolocalization, browser version, screen size, operating system, and language. 

    Route requests from the user set to the new version. 

    Check for bugs, efficiency, performance, and issues. 

    Once all issues are resolved, route all traffic to the new version. 

Rollbacks can be implemented, but downtime can impact the user.

Pros
	

Cons

Multiple versions can run in parallel
	

Requires intelligent load balancer

Full control over traffic distribution 
	

Difficult to troubleshoot errors for a given session, distributed tracing becomes mandatory
Shadow strategy

In a shadow strategy, a “shadow version” of the application is deployed alongside the live version. User requests are sent to both versions, and both handle all requests, but the shadow version does not forward responses back to the users. This lets developers see how the shadow version performs using real-world data without interrupting user experience.

To perform a rollback, switch the environments back.

Pros
	

Cons

Performance testing with production traffic
	

Expensive (double resources) 

No user impact
	

Not a true user test, can lead to misinterpreted results

No downtime
	

Complex setup

	

Requires monitoring for two environments
Deployment strategies summary

Strategy
	

Zero Downtime
	

Real Traffic Testing
	

Targeted Users
	

Cloud Cost
	

Rollback Duration
	

NegativeUser Impact 
	

Complexity of Setup

Recreate

Version 1 is removed then version 2 is rolled out
	

X
	

X
	

X
	

•--
	

•••
	

•••
	

- - -

Ramped

Version 1 is replaced by a slow rollout of version 2
	

✓
	

X
	

X
	

•--

	

•••

	

•--

	

•--

Blue/Green

Version 2 is released together with version 1, then the traffic is switched to version 2
	

✓
	

X
	

X
	

•••

	

- - -

	

••-

	

••-

Canary

Version 2 is first released to a subset of users, then fully rolled out when production ready
	

✓
	

✓
	

X
	

•--

	

•--

	

•--

	

••-

A/B Testing

Version 2 is only released to a subset of users with specific traits
	

✓
	

✓
	

✓
	

•--

	

•--

	

•--

	

•••

Shadow

Version 2 receives real-world traffic together with version A but doesn’t respond to users
	

✓
	

✓
	

X
	

•••
	

- - -
	

- - -
	

•••

 To create a good strategy:

    Consider the product type and the target audience 

    Shadow and canary strategies use live user requests, as opposed to using a sample of users.  

    The A/B testing strategy is useful if the version of the application requires minor tweaks or UI feature changes. 

    The blue/green strategy is useful if your version of the application is complex or critical and needs proper monitoring with no downtime during deployment. 

    The canary strategy is a good choice if you want zero downtime and are comfortable exposing your version of the application to the public.  

    A rolling strategy gradually deploys the new version of the application. There is no downtime, and it is easy to roll back. 

    The recreate strategy is a good choice if the application is not critical and users aren’t impacted by a short 
Proxy 	In computing, a proxy is a server that acts as an intermediary for a remote service.
ReplicaSet 	A ReplicaSet (aims to) maintain a set of replica Pods running at any given time.
Workload 	A workload is an application running on Kubernetes.


