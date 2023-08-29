
#devops #containers #AWS #cloud #containerOrch

Elastic Container Service is a Container Orchestration Tool provided by AWS (See [[Containers]] and [[Container Orchestration]]).

- Manages Lifecycle of Container

On AWS if you want somewhere to run your containers in the AWS cloud you might consider creating a ECS Cluster. This will be managed by AWS and basically consist of a Control plane that manages the virtual machines running your containers. 

The actual virtual machines running your containers will be [[EC2]] Instances that have a container runtime and ECS agent installed. 

Another Options for this would be to run your Containers on [[Fargate]] Instances.