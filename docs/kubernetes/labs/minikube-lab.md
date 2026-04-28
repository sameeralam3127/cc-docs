# Kubernetes Lab with Minikube

This page gives a simple Minikube workflow for local Kubernetes practice.

## Suggested Flow

1. Start Minikube with your preferred driver.
2. Confirm the cluster and current namespace context.
3. Apply a sample Deployment and Service.
4. Check rollout status and logs.
5. Stop or delete the cluster when the exercise is finished.

## Quick Validation

```bash
minikube start --driver=docker
kubectl get nodes
kubectl get pods -A
kubectl rollout status deployment/my-app
```
