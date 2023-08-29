#devops #containers #k8s #dataBases 

### what is a stateful application?

A kubernetes component that is used for stateful applications.

A stateful application is any application that stores data in order to keep track of state. For example databases (See [[Databases]]) 

In contrast stateless applications do not keep a record of state and each interaction is handled in an isolated way with the data that comes with the interaction. 

In kubernetes Stateless applications are deployed with Deployments (See [[Main k8s Components]]) Whereas Stateful applications are deployed with the Stateful Set component. 

### Deployment Vs Stateful Set

- replicating stateful apps is more difficult 
- it also has other requirements

Reason being that we cant just Spin up identical replicas of a stateful pod. They need a unique identity (sticky Identity, see [[Sticky Sessions]]). 

We want to avoid any data inconsistencies. So what we do is have a mechanism that decides only one pod is allowed to write to the data a one time. This pod will be referred to as the master. 

Also these pods are not using the same Physical storage, they all use replicas of the physical storage. 

You need to make sure you configure the cloning and data synchronization between stateful set pod replicas. 

Also making sure the persistent volumes (Storage class , see [[K8s Volumes]]) are set up and configured.

And making sure the remote storage is backed up and available.