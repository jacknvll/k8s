# Summary

This project is a learning repository as I follow a Udemy course with a syllabus on par with the "Certified Kubernetes Administrator" (CTA) certificate.


# Helpful Commands
```
kubectl get pods
kubectl run nginx --image=nginx
```

```
vim config.yml
kubectl apply -f config.yml
```
Delete pod by name:
```
kubectl delete pod redis123
```

Shows the Node for each Pod:
```
kubectl get pods -o wide
```
## Real example:
Using example in this directory:

```vim pod-definition.yml```

Create and apply definition:

```kubectl apply -f pod-definition.yml```

Find the pod:
```kubectl describe pod myapp-pod```

# Tool Alias
Sometimes writing ```kubectl``` all the time can be burdensome. You could also setup an 'alias' to shorten the command to something quicker to type.

For exaple:
```
alias k='kubectl'
```
Now you only need to type ```k``` to execute the kubectl tool.

# Deployments Inline
You can create deployments directly on the CLI terminal and let the tool generate the YAML configuration file for you. This can be a quicker solution than writing out a whole config file.
```
kubectl create deployment httpd-frontend --image=httpd:2.4-alpine --replicas=33 -o yaml > httpd-deployment.yaml
```

Another, for Pods:
```
kubectl run redis --image=redis -n=dev
```

get pods in all namespaces:
```
kubectl get pods -A
```

# Services
The Service API provides loose coupling between microservices in an application hosted in K8s.

There are three types of services:
1. NodePort - acts as a proxy, forwarding traffic from node to pod.
2. ClusterIP - internal-only virtual IP address for communication between different components within a Kubernetes cluster.
3. LoadBalancer - if hosted in a major cloud provider, it will automatically enable their 'Load Balancer' service and assign a Public IP address to the K8s service; you can find the Public IP using the ```kubectl get service serviceName```.

The internal DNS name for a service follows the format:

```
<service-name>.<namespace>.svc.cluster.local
```