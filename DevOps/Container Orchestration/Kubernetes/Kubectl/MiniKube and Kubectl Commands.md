#devops #containers #k8s #tools 

### What is MiniKube? 

A Single Node k8s Cluster where the master and worker processes both run on one Node (see [[Kubernetes Architecture]] for detailed explanations of master/node processes). Used for testing and learning processes. 

### How are we going to interact with our Cluster?

Kubectl ! 
A command line tool for k8s. Kubectl will talk to the API Server so you can control your kubernetes cluster.
### Local Setup

After following the relevant instructions online for both minikube and kubectl,  run `minikube start` to start our cluster. Then `kubectl get nodes` to check what nodes we have running in our cluster.

We can also check the cluster status by running `minikube status` - this shows us the running kubernetes processes

### Main Kubectl commands

#### Get Status of Components and Create and Edit Pods

- `kubectl get nodes` - display the running nodes in our cluster
- `kubectl get pods` - display the pods in our cluster
- `kubectl get services` - display services

Now we have viewed some basic info around our cluster we want to actually deploy a pod. But in K8s we work with deployments (blueprints for pods) which can be created as follows:
- `kubectl create deployment NAME --image=image [--dry-run] [options]`

For example 

`kubectl create deployment deploy-nginx --image=nginx` 

This will create a blueprint for a pod (deployment) running the latest nginx image as a container. Executing this command will start the pod.

Now running `kubectl get pod` we can see the running pod with a name constructed as follows:

`<deployment-name>-<replicaset-Id>-<pod-Id>`

#### Replica Set

If we now run `kubectl get replicaset` we can see the information of how our deployments are configured to be replicated in our cluster. By default our deployment is not replicated but in our deployment creation command we can specify replicas in the `[options]` 

### Layers of abstraction

DEPLOYMENTS *manages a* REPLICASETS *manages a* POD *is an abstraction of a* CONTAINER 

Remember, everything below a deployment is managed by kubernetes, we only work with deployments and above.


### Edit a running Deployment

back to our example nginx deployment. Say now we want to edit our running deployment. We can run `kubectl edit deployment NAME` in our case NAME = deploy-nginx. 

This then takes us to an auto-generated YML config file with some default values.  We can edit this file and save to make changes apply to our running deployment.

### Debugging Pods

To see Pod Logs run `kubectl logs NAME` Where NAME is the full name of the pod.

Additionally we can get other information about a pod by running `kubectl describe pod NAME`

Another useful one is `kubectl exec -it POD_NAME -- bin/bash` This will start an interactive bash terminal inside the application container running in this pod.  This is useful when we want to manually inspect or test what is going on inside the container of our running pod.

### Deleting Pods

To remove a running pod we need to delete the deployment using `kubectl delete deployment NAME` where NAME is the name of the deployment.

### Note:

Basically all CRUD Operations happen on the Deployment level !

### Working with kubernetes configuration files

In practice the above operations are very manual so we work with the K8s configuration files when we are defining how we want the deployments in our cluster to look like.

Once we have our configuration file as we want it, we tell kubectl to execute from that file using the following command. 

`kubectl apply -f [FILE_NAME]` 

Here is an example of a nginx configuration file

```YML
apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx-deployment
  labels:
    app: nginx
spec:
  replicas: 2
  selector:
    matchLabels:
      app: nginx
  template:
    metadata:
      labels:
        app: nginx
    spec:
      containers:
        - name: nginx
          image: nginx:1.16
          ports:
            - containerPort: 80
```

save this file with a .yaml file extension 

#### Important Points

- If we run our `kubectl apply` command and k8s can see that the deployment doesn't exist, it will create one. Furthermore, if we run our `kubectl apply` command and the deployment does exist it will know to update the running deployment with any changes to the configuration file.

- Also `kubectl apply` doesn't just work with deployments ! It works with other k8s resources such as volumes, services and so on. Just Change the config file accordingly.  

For a more in-depth explanation of these config files see [[YAML Configuration For Kubernetes]]