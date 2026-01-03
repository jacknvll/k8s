# Manual Scheduling
If no scheduler exists, use pod Binding.
Or define the nodeName in the yml config. 

Determine if the scheduler service is running:
```
kubectl get pods -n kube-system
```

Move a pod from one node to another (edit the nodeName in the file first)
```
kubectl replace -f pod.yaml --force
```

# Labels and Selectors
Get all resources with ```prod``` env label
```
k get all --selector env=prod
```

Get specific components with the ```prod``` env label:
```
k get pods,replicasets,services --selector env=prod
```

Filter by multiple labels:
```
k get pod --selector env=prod,bu=finance,tier=frontend
```

In a ReplicaSet, the selector must include at least one label matching what is being deployed. Otherwise will get a similar error:
*The ReplicaSet "replicaset-1" is invalid: spec.template.metadata.labels: Invalid value: {"tier":"nginx"}: `selector` does not match template `labels`*

# Taints and Tolerants
A taint is a rule allowing certain pods to be scheduled to a Node. However, it does not guarantee the Pod will only go to that Node!

Toleration is defined within a Pod. This could be labelling. 

To taint a node, follows the format:
```
k taint nodes node-name key=value:taint-effect
```

To remove the taint on a node:
```
k taint nodes node-name key-
```

Remove taint with key and effect if one exists:
k taint nodes node-name key:effect-

To find if a node has a taint:
```
k describe node node-name | grep Taint
```

There are three taint effects:
1. NoSchedule - does not allow intolerant pods
2. PreferNoSchedule - best attempt to not allow intolerant pods.
3. NoExecute - existing pods will be evicted if not tolerant.