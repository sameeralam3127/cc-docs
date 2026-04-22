# Kubernetes Lab with Podman

Use this page for Podman-based local Kubernetes experiments where your environment supports it.

## Suggested Flow

1. Confirm Podman and `kubectl` are installed.
2. Start the local cluster or lab environment.
3. Deploy a small test workload with a pinned image tag.
4. Validate networking, logs, and rollout behavior.
5. Tear down the environment when finished.

## Verification Commands

```bash
kubectl get nodes
kubectl get pods -A
kubectl describe pod <pod-name>
kubectl logs <pod-name>
```
