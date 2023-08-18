#devops #containers #k8s 

### What is Helm?

##### As a Package Manager

- Package Manager for Kubernetes - convenient way of packaging k8s YAML files (see [[YAML Configuration For Kubernetes]]) and distributing them from a public and private registry. 
- A Use case for this would be: say for example you have build a kubernetes cluster and you want to deploy Elastic Stack to get the logs of your system. Instead of writing the YAML configuration for all the components you will need (See [[Main k8s Components]]) someone on the internet has probably created a helm chart for this which you download and apply.
- Also useful for re-building your infra

##### As a Templating Engine

- Say we are deploying microservices into our kubernetes cluster. A lot of the configuration files for the deployments and services will have the same template with some dynamic values. With Helm you can Define a common blueprint and specify with placeholders which fields you want to be dynamic. 

### Helm Chart File Structure

```
mychart/ # root dir
	Chart.yaml # meta info about chart
	values.yaml # values for template files
	charts/ # other chart dependencies
	templates/ # template yaml files
```

To install a Helm chart `helm install <chart_name>`

