#devops #containers #k8s 

### Pod

- Smallest unit of K8s
- Abstraction over a container (we dont HAVE to work with [[Docker]] for example)
- one pod runs one Application container
- Each Pod gets its own Internal IP address (see [[IP addresses]])
- Pods are Ephemeral and new IP address are assigned every time a pod restarts, which is very annoying and therefore brings us to the next main component. 

### Services

- A static IP address that can be attached to a pod
- Lifecycle of the service and pod are NOT connected
- also handles load balancing

### Ingress

- Accepts external requests and forwards them to internal Services.

### Config Map 

- external configuration of your application
- dont put credentials in Plain Text in config maps

### Secret

- used to store secret data for configurations 
- encoded in base64

### Volumes

- Attaches a physical storage to your running pod, this way if the pod running a db is restarted then the data is not lost.
- could be on the local machine or a remote location
- data is persisted 

### Deployments 

- a blueprint for pods
- used to define how many replicas of pods you need 
- also for other configurations around pods
- CAN NOT replicate a DB using deployments due to data inconsistencies 

### Stateful Set

- Deployments for stateful applications (data bases)
- this can be difficult!
- For this reason DBs are often hosted outside of k8s cluster

