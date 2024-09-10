```markdown
# Kubernetes Namespace and Deployment Guide

## What is a Namespace in Kubernetes, and Why is it Used?
A namespace in Kubernetes is a logical partition within a cluster that allows you to divide resources into named groups. It is used to isolate resources between different teams or projects within the same cluster, making it easier to manage different environments like development, testing, and production without conflicts.

## How to Create a New Namespace in Kubernetes Using the kubectl Command
```bash
kubectl create namespace <namespace-name>
```

## How to List All Namespaces in a Kubernetes Cluster
```bash
kubectl get namespaces
```

## What is the Default Namespace in Kubernetes? What Happens if You Do Not Specify a Namespace When Deploying a Resource?
The default namespace is `default`. If you do not specify a namespace when deploying a resource, it will be deployed in the default namespace.

## How to Delete a Namespace in Kubernetes? What Happens to the Resources Within It?
```bash
kubectl delete namespace <namespace-name>
```
When you delete a namespace, all resources within it are also deleted.

## How to Switch Between Namespaces While Using the kubectl Command
```bash
kubectl config set-context --current --namespace=<namespace-name>
```

## How to Create a Kubernetes Deployment in a Specific Namespace
```bash
kubectl create deployment <deployment-name> --image=<image-name> --namespace=<namespace-name>
```

## Can Two Different Namespaces Have Resources with the Same Name? Explain Your Answer.
Yes, two different namespaces can have resources with the same name because namespaces isolate resources, allowing for name duplication across different namespaces.

## How to Check the Resource Quotas and Limits for a Specific Namespace
```bash
kubectl get resourcequotas --namespace=<namespace-name>
kubectl describe resourcequota <resourcequota-name> --namespace=<namespace-name>
```

## How to Configure a kubectl Context to Always Use a Specific Namespace by Default
```bash
kubectl config set-context --current --namespace=<namespace-name>
```

## Create a YAML File to Define a New Namespace Called dev-environment. Deploy It Using kubectl.
Create a file named `dev-environment.yaml` with the following content:
```yaml
apiVersion: v1
kind: Namespace
metadata:
  name: dev-environment
```
Deploy it using:
```bash
kubectl apply -f dev-environment.yaml
```

## Write a Command to Deploy a Pod Named test-pod Running the nginx Image into a Namespace Called testing
```bash
kubectl run test-pod --image=nginx --namespace=testing
```

## List All the Pods Running in a Namespace Called production
```bash
kubectl get pods --namespace=production
```

```

