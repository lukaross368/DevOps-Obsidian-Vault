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



Here are a couple of basic examples of some configuration files

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

In this Deployment config file we can see that in the `spec:` section we have `template:` which contains its own spec. This is since deployments are blueprints for Pods we want the specification of our pods to be contained in our deployment config.