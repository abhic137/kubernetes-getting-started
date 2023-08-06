# kubernetes-getting-started

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

