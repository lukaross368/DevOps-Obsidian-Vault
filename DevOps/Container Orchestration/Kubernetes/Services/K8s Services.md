#k8s #devops #containers 

### What is a Kubernetes Service and when do we need it?

Each pod gets its own Internal IP address (See [[IP addresses]]). But pods are ephemeral and when they are restarted they will get another random IP. Services are a way of consistently communicating with pods even when they die or are restarted. Services are put in front of pods or multiple pods and they also handle load balancing.  

Services are a great abstraction that provide loose coupling for intra-cluster networking.

### Service Types

#### ClusterIP Service

- Default service type
- 'Internal Service'
- Targeted by an ingress
- Assigned to pods with selectors and target port

You can also have multiple Ports open on one ClusterIP Service for example
![[multiPortIP.png]]

#### Headless Service

What if we want to talk to a specific Pod and not get randomly load balanced between pods ever time we make a request? (Common use case would be communicating with stateful applications)

To do this we can define a Headless Service by setting the ClusterIP value in the spec of our service configuration to be 'None'.

This will make sure the service is not assigned a cluster IP address so clients of the this service can  do DNS lookups (See [[DNS]]) directly on the Individual pods its attached to. 

#### NodePort Service

The NodePort Service type assigns a static port on the worker node so clients of the node can communicate with the service from outside the cluster (Instead of using an ingress, see [[K8s Ingress]]).  This is not a very secure setup

#### LoadBalancer Service

If we use LoadBalancer Service type our service becomes externally accessible through a cloud providers LoadBalancer.  

**Key point: LoadBalancer Service is an extension of NodePort which is an extension of ClusterIP**




