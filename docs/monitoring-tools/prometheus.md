# Prometheus Guide for the Monitoring Stack

Prometheus is the core metrics and alerting engine in this monitoring lab.

## What It Does

- Scrapes metrics from configured targets
- Stores time-series data
- Evaluates alert rules
- Supplies metrics to Grafana

## Important Files

- `prometheus/prometheus.yml`
- `prometheus/rules/alerts.yml`

## Main Scrape Targets

- Prometheus
- Alertmanager
- Node Exporter
- cAdvisor
- Blackbox Exporter
- Blackbox HTTP probe jobs

## Why This Layout Works

It combines host metrics, container metrics, and endpoint checks in one place. That gives a more complete view than using only one exporter type.

## Example Alerts

- `TargetDown`
- `HostHighCPU`
- `HostHighMemory`
- `ContainerHighCPU`
- `ContainerHighMemory`
- `SyntheticProbeFailed`

## Practical Improvements

- Add severity labels such as `warning` and `critical`
- Add `for:` windows to reduce alert noise
- Add ownership labels for teams or services
- Add recording rules for repeated expensive queries

## Quick Check

```bash
docker compose logs -f prometheus
curl http://localhost:9090/-/healthy
curl http://localhost:9090/api/v1/targets
```
