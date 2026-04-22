# Blackbox Exporter Synthetic Monitoring Guide

This page explains how Blackbox Exporter is used in the monitoring repository for endpoint probing.

## Key File

- `blackbox/blackbox.yml`

## What Blackbox Exporter Does

Unlike Node Exporter or cAdvisor, Blackbox Exporter does not collect host or container resource metrics directly.

Instead, it performs probe-style checks such as:

- HTTP reachability
- Response success or failure
- Basic latency visibility

## How It Is Used in This Stack

The repository uses Blackbox Exporter to probe internal HTTP targets such as:

- Grafana
- Prometheus
- cAdvisor
- Alertmanager
- Loki

This complements normal metrics scraping because a service can look healthy internally while still being unreachable to a client or probe.

## Why Synthetic Checks Matter

Synthetic monitoring answers a different question:

- Exporter metrics answer: "Is the service reporting metrics?"
- Blackbox answers: "Can something actually reach and use the endpoint?"

Both are valuable.

## Good Metrics to Watch

- Probe success
- Probe duration
- HTTP status result
- Failure frequency over time

## Good Follow-Up Improvements

- Add external URL checks
- Add HTTPS validation
- Add DNS and TCP probe modules
- Label probe targets by service and environment

## Verification

```bash
docker compose logs -f blackbox
curl http://localhost:9115
```
