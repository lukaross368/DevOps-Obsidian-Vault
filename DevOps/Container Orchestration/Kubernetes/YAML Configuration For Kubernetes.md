#devops #k8s #containers 

### Overview 

- 3 main parts to the config file
- Connecting deployments to service to pods
- Example

### Three main parts of the config file

Outside of the Main parts of the config we define the API version (for each component there is a different API version) and the 'kind' of resource we are creating (i.e. Service, deployment, etc)

The three main parts are

1) Metadata
2) Specification
3) Status (automatically generated and added by Kubernetes!)

Kubernetes gets the Status of the components from the etcd  (see: [[Main k8s Components]])

Best practice Is to keep these configuration files in version control with application code or in its own repository. 

Deployment Configuration
```yaml
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
        - containerPort: 8080
```

In this Deployment config file we can see that in the `spec:` section we have `template:` which contains its own meta data and spec. This is since deployments are blueprints for Pods we want the specification of our pods to be contained in our deployment config.

#### Connecting Components

To connect components we need to know more about labels, selectors and ports.

- Metadata contains labels
- Specification contains selectors

##### Connecting Deployments to Pods

Take our example file above.  As we can see, we give our components (in this case we define one pod and one deployment) the following key-value pair for labels:

```yaml
  metadata:
	  labels:
	    app: nginx
```

It lives in the Metadata for the deployment and also the same value below in the metadata for the pod (also contained in the deployment config file under the `template:` section)

Now to create the connection between our Pod and our deployment, we define a `matchLabels:` tag under a selector in the Specification. We say that we want all labels matching `app:nginx` to be attached to our Component (in this case deployment). 

```yaml
spec:
  selector:
    matchLabels:
      app: nginx
```

So we basically tag our component we want to connect (in this case a pod) and then define on the parent component, the resources with a specific tag we want to connect (in this case we connect our pod to our deployment). 

##### Connecting Service to Deployments

Now we have attached our Pod blueprint to a deployment we want to attach a Service to that deployment and we do it in a similar way. Since we labelled our Deployment with `app:nginx` before,  we define our selector to look for components with the `app:nginx` key-value pair.

Service Configuration
```yaml
apiVersion: v1
kind: Service
metadata:
  name: nginx-service
spec:
  selector:
    app: nginx
  ports:
    - protocol: TCP
      port: 80
      targetPort: 8080
```

#### Note

- To see the internal IP addresses of your Pods use `kubectl get pods -o wide`

- If we Apply both of the config files above and we want to see the 3rd main part of the config that is auto generated (the Status) we can run:
	
	`kubectl get <component> <component-name> -o yaml`

 and the result will look like this 

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  annotations:
    deployment.kubernetes.io/revision: "1"
    kubectl.kubernetes.io/last-applied-configuration: |
      {"apiVersion":"apps/v1","kind":"Deployment","metadata":{"annotations":{},"labels":{"app":"nginx"},"name":"nginx-deployment","namespace":"default"},"spec":{"replicas":2,"selector":{"matchLabels":{"app":"nginx"}},"template":{"metadata":{"labels":{"app":"nginx"}},"spec":{"containers":[{"image":"nginx:1.16","name":"nginx","ports":[{"containerPort":80}]}]}}}}
  creationTimestamp: "2023-08-16T13:46:59Z"
  generation: 1
  labels:
    app: nginx
  name: nginx-deployment
  namespace: default
  resourceVersion: "5874"
  uid: ce8ed730-8c25-4fb4-ad4e-50cb58187f6e
spec:
  progressDeadlineSeconds: 600
  replicas: 2
  revisionHistoryLimit: 10
  selector:
    matchLabels:
      app: nginx
  strategy:
    rollingUpdate:
      maxSurge: 25%
      maxUnavailable: 25%
    type: RollingUpdate
  template:
    metadata:
      creationTimestamp: null
      labels:
        app: nginx
    spec:
      containers:
      - image: nginx:1.16
        imagePullPolicy: IfNotPresent
        name: nginx
        ports:
        - containerPort: 80
          protocol: TCP
        resources: {}
        terminationMessagePath: /dev/termination-log
        terminationMessagePolicy: File
      dnsPolicy: ClusterFirst
      restartPolicy: Always
      schedulerName: default-scheduler
      securityContext: {}
      terminationGracePeriodSeconds: 30
status:
  availableReplicas: 2
  conditions:
  - lastTransitionTime: "2023-08-16T13:47:00Z"
    lastUpdateTime: "2023-08-16T13:47:00Z"
    message: Deployment has minimum availability.
    reason: MinimumReplicasAvailable
    status: "True"
    type: Available
  - lastTransitionTime: "2023-08-16T13:46:59Z"
    lastUpdateTime: "2023-08-16T13:47:00Z"
    message: ReplicaSet "nginx-deployment-57d98f69f6" has successfully progressed.
    reason: NewReplicaSetAvailable
    status: "True"
    type: Progressing
  observedGeneration: 1
  readyReplicas: 2
  replicas: 2
  updatedReplicas: 2
```

