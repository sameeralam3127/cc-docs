# Kubernetes Lab with Podman Guide

This page gives a simple Podman-based workflow for local Kubernetes experiments where the environment supports it.

## Suggested Flow

1. Confirm Podman and `kubectl` are installed.
2. Start the local cluster or lab environment.
3. Deploy a small workload with a pinned image tag.
4. Validate networking, logs, and rollout behavior.
5. Tear down the environment after testing.

## Quick Validation

```bash
kubectl get nodes
kubectl get pods -A
kubectl describe pod <pod-name>
kubectl logs <pod-name>
```
