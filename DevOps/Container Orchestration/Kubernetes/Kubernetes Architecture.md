#devops #containers #k8s 

### Node Processes

One of the main components of a k8s cluster are its Worker Nodes.  Each Node will have multiple Pods running on it. To achieve this each Node must have three processes running.  These are; 
- Container Runtime (for example [[Docker]])
- Kubelet - A Kubernetes Process that schedules the containers. It interfaces with the Container Runtime and the Node machine. Kubelet starts the pod and assigns resources to it 
- Kube Proxy - responsible for forwarding requests from services to pods. It does this in an intelligent way with low overhead.

Nodes are the Servers in your k8s Cluster that actually do the work. 

### How do we Interact with our cluster of Nodes? 

- Schedule pods?
- Monitor?
- Re-Schedule/Re-Start pods?
- Join a new Node?

Managing is done by a Master Node

### Master Node Processes

Each master node need 4 processes that will help in controlling the cluster state and worker nodes.

- API Server - as a user when we want to deploy a new application to our cluster we interact with the cluster via the API server (K8s CLI or Dashboard for example). Think of it as a Cluster Gateway which also acts as a gatekeeper for authentication. 
- Scheduler - Based on a request being handed over by the API server, decides where a new pod should be started. Does this in an intelligent way based on resources. Note that the actual pod scheduling is done on the worker-node side by the kubelet.  
- Controller Manager - Detects state changes of the cluster (crashing of pods for example). Makes requests to the scheduler to try and restore state. 
- etcd - key value store of the cluster state. All other master node processes reference the etcd for the info they need. 

In practice K8s cluster will be made up of multiple Master Nodes with Load-Balancing between the API Server and in this case the etcd will form a distributed storage. 


![[k8s.png]]

### Example Cluster Setup

![[example-k8s-setup.png]]