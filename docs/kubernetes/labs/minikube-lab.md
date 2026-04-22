# Kubernetes Lab with Minikube

Use this page for Minikube-focused hands-on exercises and quick experiments.

## Suggested Flow

1. Start Minikube with your preferred driver.
2. Verify the cluster and namespace context.
3. Apply a sample Deployment and Service.
4. Inspect rollout status and logs.
5. Stop or delete the cluster after the exercise.

## Verification Commands

```bash
minikube start --driver=docker
kubectl get nodes
kubectl get pods -A
kubectl rollout status deployment/my-app
```
