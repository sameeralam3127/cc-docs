# Monitoring Stack with Prometheus, Grafana, Alertmanager, Loki, and Exporters

This page documents the monitoring stack from the GitHub repository [sameeralam3127/Monitoring](https://github.com/sameeralam3127/Monitoring).

The repository is a Docker-based observability lab that combines metrics, logs, alerting, and synthetic health checks in one stack. It is a much better foundation than the older single-host Podman walkthrough because it reflects a fuller real-world monitoring setup.

!!! info "What this stack includes"
    - Prometheus for metrics scraping and alert evaluation
    - Grafana for dashboards and visualization
    - Alertmanager for routing alerts
    - Node Exporter across multiple Linux containers for host-style metrics
    - cAdvisor for container metrics
    - Blackbox Exporter for HTTP probing
    - Loki for log storage
    - Promtail for log collection

!!! tip "Repository"
    Source: [https://github.com/sameeralam3127/Monitoring](https://github.com/sameeralam3127/Monitoring)

!!! warning "Lab vs production"
    This repository is excellent for learning and demos. For production, you would usually add stronger secret handling, persistent storage design, authentication hardening, backup strategy, and external notification integrations.

## Monitoring Section Map

- [Monitoring overview](overview.md)
- [Prometheus deep dive](prometheus.md)
- [Grafana walkthrough](grafana.md)
- [Alertmanager routing](alertmanager.md)
- [Loki and Promtail logging](logging.md)
- [Blackbox Exporter guide](blackbox.md)
- [Troubleshooting](troubleshooting.md)

---

## Why This Repo Is Useful

Many monitoring tutorials stop at Prometheus plus Grafana. This repo goes further by covering the main observability layers together:

- Metrics from Prometheus, Node Exporter, and cAdvisor
- Logs with Loki and Promtail
- Alerts with Alertmanager
- Synthetic checks with Blackbox Exporter
- Dashboards pre-provisioned in Grafana

That makes it a strong hands-on project for DevOps and SRE learning because it shows how the pieces fit together instead of teaching each tool in isolation.

---

## Repository Structure

The repository includes these top-level components:

- `prometheus/` for scrape configuration and alert rules
- `grafana/` for provisioning and dashboards
- `alertmanager/` for alert routing configuration
- `blackbox/` for synthetic probe definitions
- `loki/` for log storage configuration
- `promtail/` for log collection configuration
- `docker-compose.yml` for orchestrating the full stack
- `Dockerfile` for the Linux container image used in the demo
- `grafana-dashboard.json` for dashboard export

---

## Services and Ports

Once the stack is running, the repo exposes these services locally:

- Grafana on `http://localhost:3000`
- Prometheus on `http://localhost:9090`
- Alertmanager on `http://localhost:9093`
- cAdvisor on `http://localhost:8080`
- Blackbox Exporter on `http://localhost:9115`
- Loki ready endpoint on `http://localhost:3100/ready`

Node Exporter containers are exposed on ports `9101` through `9110`.

---

## Prerequisites

Before starting the stack, make sure you have:

- Docker installed
- Docker Compose available through `docker compose`
- Internet access during the first build

Verify your environment:

```bash
docker --version
docker compose version
```

---

## Setup

### 1. Clone the repository

```bash
git clone https://github.com/sameeralam3127/Monitoring.git
cd Monitoring
```

### 2. Start the full stack

```bash
docker compose up -d --build
```

This does a few things in one command:

- Builds the demo Linux container image
- Starts multiple Node Exporter-backed Linux containers
- Starts Prometheus, Grafana, Alertmanager, cAdvisor, Blackbox Exporter, Loki, and Promtail
- Creates persistent Docker volumes for core services

### 3. Verify the stack

```bash
docker compose ps
```

### 4. Open the services

- Grafana: [http://localhost:3000](http://localhost:3000)
- Prometheus: [http://localhost:9090](http://localhost:9090)
- Alertmanager: [http://localhost:9093](http://localhost:9093)
- cAdvisor: [http://localhost:8080](http://localhost:8080)
- Blackbox Exporter: [http://localhost:9115](http://localhost:9115)

Grafana default login:

- Username: `admin`
- Password: `admin`

---

## Grafana Setup

Grafana is already provisioned in the repository, so you do not need to add data sources manually after startup.

The repo provisions:

- `grafana/provisioning/datasources/datasources.yml`
- `grafana/provisioning/dashboards/dashboards.yml`
- `grafana/dashboards/advanced-monitoring-dashboard.json`

After login, you should already have:

- Prometheus as a data source
- Loki as a log data source
- An advanced monitoring dashboard ready to use

---

## Prometheus Configuration

Prometheus configuration is stored in:

- `prometheus/prometheus.yml`
- `prometheus/rules/alerts.yml`

Configured scrape jobs include:

- `prometheus`
- `alertmanager`
- `node_exporter`
- `cadvisor`
- `blackbox-exporter`
- `blackbox-http`

Example alerts in the repo include:

- `TargetDown`
- `HostHighCPU`
- `HostHighMemory`
- `ContainerHighCPU`
- `ContainerHighMemory`
- `SyntheticProbeFailed`

---

## Logging with Loki and Promtail

The repository also includes a log pipeline.

Configuration files:

- `loki/loki-config.yml`
- `promtail/promtail-config.yml`

Promtail is configured to collect:

- Host log files from `/var/log`
- Docker container logs from `/var/lib/docker/containers`

This is useful because it lets you view both metrics and logs from the same Grafana interface.

---

## Blackbox Monitoring

Blackbox Exporter is configured through:

- `blackbox/blackbox.yml`

It is used to probe internal HTTP endpoints such as:

- Grafana
- Prometheus
- cAdvisor
- Alertmanager
- Loki

This gives you synthetic monitoring on top of regular metrics scraping.

---

## Useful Commands

Start the stack:

```bash
docker compose up -d --build
```

Stop the stack:

```bash
docker compose down
```

Stop the stack and remove volumes:

```bash
docker compose down -v
```

Check running services:

```bash
docker compose ps
```

View logs for a specific service:

```bash
docker compose logs -f prometheus
docker compose logs -f grafana
docker compose logs -f promtail
```

Restart a service:

```bash
docker compose restart grafana
```

---

## What Makes This Repo Better Than a Basic Monitoring Demo

- It covers metrics, logs, alerts, and probes in one project
- It uses Docker Compose for repeatable startup
- It includes ready-made Grafana provisioning
- It includes alert rules instead of stopping at dashboards
- It demonstrates both host-style and container-level monitoring

For someone building DevOps documentation, this repo is worth highlighting because it feels much closer to a practical observability lab than a minimal single-tool setup.
