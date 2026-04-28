# Kubernetes Lab with Docker Desktop

This page gives a simple flow for running Kubernetes practice workloads with Docker Desktop.

## Suggested Flow

1. Enable Kubernetes in Docker Desktop.
2. Confirm the current context with `kubectl config current-context`.
3. Check cluster health with `kubectl get nodes`.
4. Deploy a small sample workload and expose it with a Service.
5. Clean up the resources after testing.

## Quick Validation

```bash
kubectl cluster-info
kubectl get nodes
kubectl get pods -A
```
