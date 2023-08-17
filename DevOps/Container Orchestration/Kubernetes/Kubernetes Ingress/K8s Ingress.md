#devops #k8s #containers #networking 

### Why do we need ingress?

In order to route traffic to your application but not expose the port and IP.

### Ingress VS External Service

External Service Configuration File (For Info on Services see [[Main k8s Components]])

```yaml
apiVersion: v1
kind: Service

metadata:
	name: myapp-external-service

spec:
	selector:
		app: myapp
	type: LoadBalancer # external service type
	ports:
		- protocol: TCP
		- port: 8080
		- targetPort: 8080
		- nodePort: 35010
```

VS 

Ingress Configuration File

```yaml
apiVersion: networking.k8s.io/v1beta1
kind: Ingress

metadata:
	name: myapp-ingress

spec:
	rules:
	- host: myapp.com
	- http:
		paths:
		- backend:
			serviceName: myapp-internal-service
			servicePort: 8080
```

Of course if we go with the Ingress option we still need a Internal Service for it to route traffic to. 
In the case of the Ingress config about this is what it would look like

```yaml
apiVersion: v1
kind: Service

metadata:
	name: myapp-external-service

spec:
	selector:
		app: myapp
	ports:
		- protocol: TCP
		- port: 8080
		- targetPort: 8080
```

### Ingress Controller

In practice to use ingress we need something called an Ingress controller. This will evaluate and process the ingress rules. It runs in a Pod.

There are many Third party options for your Ingress Controller, it will act as the entry point to your cluster.

