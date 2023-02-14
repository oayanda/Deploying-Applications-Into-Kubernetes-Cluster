# Exploring Common Objects in K8s

Pods

A pod is the smallest unit of kubernete cluster. It has a one to one relationship with a container. This means a pod should only hold one container. However, in some case, a pod can hold more than one related containers. To deploy an object in k8s, YAML file manifest is required with specific sections.

Let's explore how to deploy a simple nginx pod.

**Deploying a Nginx Pod**

*Create a yaml file - nginx-pod.yaml*

```bash
# Kubernetes api version
apiVersion: v1

# Type of kubernetes object to created
kind: Pod

# Provides information about the resource like name, label
metadata:
name: nginx-pod

# Consists of the core information about Pod
spec:
containers:
- image: nginx:latest
name: nginx-pod
ports:
- containerPort: 80
  protocol: TCP
```

```bash
# Use this shortcut for typing kubectl all time
alias k=kubectl
```

```bash
# Create a nginx pod
k create -f nginx-pod.yaml

# View the created pod
k get pods
```

![pods](./images/1.png)

```bash
# Get more information about the pod
k describe pod nginx-pod
or 
k get pod nginx-pod -o yaml
```

> The nginx image used in the yaml file is was pull from the docker hub, in some cases the intended repo is explicitly stated.

![pods](./images/2.png)
