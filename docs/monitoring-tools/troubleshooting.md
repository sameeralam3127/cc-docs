# Troubleshooting Common Docker Compose Monitoring Issues

This page collects common issues you may hit while running the monitoring stack locally with Docker Compose.

## 1. Containers Start but Grafana Has No Data

Check:

- Prometheus is healthy
- Targets are up in Prometheus
- Grafana data sources loaded correctly

Useful commands:

```bash
docker compose ps
docker compose logs -f prometheus
docker compose logs -f grafana
```

## 2. Prometheus Targets Show Down

Check:

- Exporter container names and ports
- Docker networking between services
- Scrape target definitions in `prometheus/prometheus.yml`

Useful checks:

```bash
curl http://localhost:9090/api/v1/targets
docker compose logs -f prometheus
```

## 3. Loki Is Running but Logs Do Not Appear

Check:

- Promtail can read configured paths
- Loki is healthy
- Grafana Loki data source is configured

Useful checks:

```bash
docker compose logs -f promtail
docker compose logs -f loki
curl http://localhost:3100/ready
```

## 4. Blackbox Probes Fail

Check:

- The target endpoint is reachable
- Probe target names are correct
- Docker service networking resolves correctly
- `blackbox/blackbox.yml` matches the expected module and protocol

## 5. Port Conflicts on the Host

This is common if local services already use ports like `3000`, `8080`, or `9090`.

Check:

- Whether another local app is already bound to the same port
- Whether you need to change host port mappings in `docker-compose.yml`

## 6. Rebuild Issues After Config Changes

Sometimes config changes do not appear to take effect immediately.

Try:

```bash
docker compose down
docker compose up -d --build
```

If you need a full reset:

```bash
docker compose down -v
docker compose up -d --build
```

## 7. General Debug Flow

When the stack behaves unexpectedly, use this order:

1. Check container status with `docker compose ps`.
2. Check service logs.
3. Check health endpoints.
4. Check Prometheus targets.
5. Check Grafana data sources and dashboards.
6. Rebuild only after configuration has been reviewed.
