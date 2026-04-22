# Kubernetes Lab with Docker Desktop

Use this page for Docker Desktop-specific Kubernetes lab notes.

## Suggested Flow

1. Enable Kubernetes in Docker Desktop.
2. Verify the current context with `kubectl config current-context`.
3. Confirm the cluster is healthy with `kubectl get nodes`.
4. Deploy a small sample workload and expose it with a Service.
5. Clean up the lab resources after validation.

## Verification Commands

```bash
kubectl cluster-info
kubectl get nodes
kubectl get pods -A
```
