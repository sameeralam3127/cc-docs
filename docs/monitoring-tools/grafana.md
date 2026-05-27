# Grafana Guide for the Monitoring Stack

Grafana provides the dashboards and log views for the monitoring lab.

## Important Files

- `grafana/provisioning/datasources/datasources.yml`
- `grafana/provisioning/dashboards/dashboards.yml`
- `grafana/dashboards/advanced-monitoring-dashboard.json`

## What Happens Automatically

Grafana is provisioned on startup, so you do not need to create data sources and dashboards by hand every time.

That usually gives you:

- A Prometheus data source
- A Loki data source
- A ready-made dashboard for the stack

## Why Provisioning Matters

- Keeps dashboards reproducible
- Prevents manual drift
- Makes reviews easier because changes live in Git

## What to Validate

- Prometheus data source is healthy
- Loki data source is healthy
- Dashboards load without broken panels
- Panels show useful host, container, and probe metrics

## Good Dashboard Areas

- CPU, memory, disk, and network
- Container resource trends
- Prometheus target health
- Probe success rate
- Recent logs from Loki
- Alert summary

## Quick Check

```bash
docker compose logs -f grafana
curl http://localhost:3000/api/health
```

Default login:

- Username: `admin`
- Password: `admin`
