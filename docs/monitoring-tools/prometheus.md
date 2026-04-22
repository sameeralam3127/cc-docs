# Prometheus Configuration Deep Dive

This page explains how Prometheus is used in the [sameeralam3127/Monitoring](https://github.com/sameeralam3127/Monitoring) repository and what each part of the configuration is responsible for.

## Key Files

- `prometheus/prometheus.yml`
- `prometheus/rules/alerts.yml`

## What Prometheus Does in This Stack

Prometheus acts as the central metrics engine for the lab.

It is responsible for:

- Scraping infrastructure and application-style targets
- Storing time-series metrics
- Evaluating alert rules
- Exposing query results to Grafana

## Scrape Jobs

The repository config includes scrape jobs for:

- Prometheus itself
- Alertmanager
- Node Exporter containers
- cAdvisor
- Blackbox Exporter
- Blackbox HTTP probe targets

This is a good design because it mixes direct infrastructure scraping with synthetic monitoring.

## Why This Layout Works

- `node_exporter` gives host-style resource data
- `cadvisor` gives container-level visibility
- `blackbox-http` verifies endpoint reachability from a user-style perspective
- Self-scraping Prometheus helps verify the monitoring system itself

## Alerts

The alert rules file includes examples such as:

- `TargetDown`
- `HostHighCPU`
- `HostHighMemory`
- `ContainerHighCPU`
- `ContainerHighMemory`
- `SyntheticProbeFailed`

These cover a strong starter set of failure conditions:

- Exporters becoming unavailable
- Host saturation
- Container saturation
- Endpoint probe failures

## Good Follow-Up Improvements

- Add severity labels like `warning` and `critical`
- Add `for:` windows to avoid noisy flapping
- Add team or service ownership labels
- Add recording rules for expensive queries
- Add environment labels if the stack grows beyond one lab

## Verification

Useful checks:

```bash
docker compose logs -f prometheus
curl http://localhost:9090/-/healthy
curl http://localhost:9090/api/v1/targets
```
