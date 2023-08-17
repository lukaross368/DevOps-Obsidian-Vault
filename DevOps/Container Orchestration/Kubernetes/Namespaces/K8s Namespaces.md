#devops #k8s #containers 

### What is  a namespace

Namespaces can be used for organising resources inside a k8s cluster. Think of a namespace as a virtual Cluster inside an actual K8s Cluster.

K8s gets by default 4 Namespaces out of the box.

Install kubectx for easy switching between kubernetes namespaces.

#### Create a Namespace

create with
`kubectl create namespace <namespace name>`

and view with
`kubectl get namespace`

But we can also create namespaces with a configuration file (best practice)

### Why do we need to use Namespaces?

#### First Use Case

Imagine if everything is in the one default namespace. If you application is complex with many resources i.e. lots of deployments and replica sets and so on, it will become confusing very quickly.

Instead a Better approach would be to group your K8s resources in name spaces for each part of your application for example 

![[kubens.png]]

#### Second Use Case

If two teams are sharing the same cluster then will end up overriding resources so its better to split the cluster into namespaces one for each team

#### Third Use Case

Also If we want to host different environments in the same cluster. For example staging and development environments. 

![[sharedresources.png]]

This way, both our environments can use shared resources.

#### Fourth Use Case

Namespaces also come in handy if we want to use a blue/green deployment strategy (See: [[Blue Green Deployment]]) in production but both production environments want to use some shared cluster resources.

#### Fifth Use Case

We can set hard limits for Compute Resources on the Namespace level (CPU, RAM, etc.).

### Key Details

- Each Namespace must define its own config map and secret (see: [[Main k8s Components]])
- services can be shared across Namespaces. To do this simply append the namespace name on the end of the URL in the reference 
- Some Components can be defined in a namespace. For example Volume and Node. These Resources live globally in the cluster. 
	Some useful commands for listing resources that are/are not bound to a namespace
	`kubectl api-resources --namespace=false`
	`kubectl api-resources --namespace=true`


### How to create Components In a Namespace

By default Components are created in the default namespace

to override this use 

`kubectl apply -f <Configuration File Name> --namespace=my-namespace`

Another way is to do it inside the config file itself (best practice).

For example

```yaml
apiVersion: v1
kind: ConfigMap
metadata:
	name: mysql-configmap
	namespace: my-namespace
data:
	db_url: mysql-service.database
```

Remember once we create resources in a non-default namespace if we want to view them with kubectl we need be explicit with our commands:

`kubectl get configmap -n my-namespace`

Otherwise kubectl only looks in the default namespace.

This is why kubectl is such a good tool. Since it switches ACTIVE namespace for you, so you don't have to explicitly say which namespace you want to work with when executing kubectl commands.