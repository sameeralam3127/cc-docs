# Loki and Promtail Logging Flow

This page explains the logging path in the monitoring repository.

## Key Files

- `loki/loki-config.yml`
- `promtail/promtail-config.yml`

## Flow Overview

The log flow is:

1. Promtail reads logs from configured sources.
2. Promtail attaches labels and forwards logs to Loki.
3. Loki stores and indexes the logs.
4. Grafana queries Loki and displays logs in dashboards or Explore view.

## Log Sources in This Repository

Promtail is configured to collect:

- Host log files from `/var/log`
- Docker container logs from `/var/lib/docker/containers`

This is useful because it gives both system-level and container-level visibility.

## Why Loki Fits Well Here

Loki is a good match for this lab because:

- It integrates cleanly with Grafana
- It focuses on labels rather than full-text indexing everywhere
- It is lighter than some large log-stack alternatives for small labs

## What to Check

- Promtail can access the configured log paths
- Loki is healthy and accepting writes
- Grafana can query the Loki data source
- Labels are meaningful enough to filter logs well

## Common Improvements

- Add cleaner labels for service, host, and environment
- Add retention settings for predictable storage growth
- Limit noisy or low-value logs
- Parse structured logs where possible

## Verification

```bash
docker compose logs -f promtail
docker compose logs -f loki
curl http://localhost:3100/ready
```
