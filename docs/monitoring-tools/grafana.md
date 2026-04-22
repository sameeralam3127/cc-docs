# Grafana Dashboard Walkthrough

This page explains how Grafana is provisioned in the monitoring repository and what to validate after the stack starts.

## Key Files

- `grafana/provisioning/datasources/datasources.yml`
- `grafana/provisioning/dashboards/dashboards.yml`
- `grafana/dashboards/advanced-monitoring-dashboard.json`

## What Happens Automatically

Grafana is pre-provisioned, which means the repo loads core configuration on startup instead of relying on manual UI steps.

That gives you:

- Prometheus as a metrics data source
- Loki as a logs data source
- A ready-made dashboard for the stack

## Why Provisioning Matters

Provisioning is important in DevOps because it makes dashboards reproducible.

Without provisioning:

- Environments drift
- Manual steps are forgotten
- Rebuilding monitoring becomes slower

With provisioning:

- Dashboards are version controlled
- Data source setup is repeatable
- Teams can review dashboard changes in Git

## What to Validate in Grafana

After login, confirm:

- Prometheus data source is healthy
- Loki data source is healthy
- The dashboard loads without broken panels
- Panels show host, container, and probe metrics

## Good Dashboard Areas to Include

- Host CPU, memory, disk, and network
- Container CPU and memory trends
- Prometheus target health
- Blackbox probe success rate
- Recent logs from Loki
- Alert state summary

## Verification

```bash
docker compose logs -f grafana
curl http://localhost:3000/api/health
```

Default login:

- Username: `admin`
- Password: `admin`
