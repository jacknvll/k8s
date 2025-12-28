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