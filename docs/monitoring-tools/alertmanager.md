# Alertmanager Routing Examples

This page explains how Alertmanager fits into the monitoring stack and how alert routing is usually structured.

## What Alertmanager Does

Alertmanager receives alerts from Prometheus and decides:

- How alerts are grouped
- Where alerts are sent
- Which alerts should be silenced or inhibited

In the repository, Alertmanager is part of the stack and is exposed on `http://localhost:9093`.

## Typical Routing Model

A practical routing model usually looks like this:

- Group alerts by service, team, or severity
- Send critical alerts immediately
- Group warning alerts to reduce noise
- Silence known maintenance windows

## Example Ideas for Routing

- Route infrastructure alerts to the platform team
- Route synthetic probe failures to the service owner
- Route low-severity alerts to email or chat digests
- Route high-severity alerts to paging tools

## Example Concepts to Add Later

- `group_by`
- `group_wait`
- `group_interval`
- `repeat_interval`
- Receiver-specific routes
- Inhibition rules to suppress child alerts during larger outages

## Operational Advice

- Avoid sending every alert directly to paging
- Separate warning and critical severities
- Add labels in Prometheus rules that make routing easier
- Test routes before depending on them during incidents

## Verification

```bash
docker compose logs -f alertmanager
curl http://localhost:9093/-/healthy
```
