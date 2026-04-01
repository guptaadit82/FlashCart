# Observability & Monitoring

## 🎯 Objective

Establish full observability for the SmartCart system using Prometheus for metrics collection, Grafana for dashboards, and AI-assisted anomaly detection to proactively identify threshold breaches and system degradation.

---

## 📋 Tasks Performed

- Configured Prometheus to scrape SmartCart backend metrics
- Built Grafana dashboards for API performance, error rates, and JVM health
- Set up alerting rules for threshold breaches
- Monitored system during performance test execution
- Used AI to detect anomalies in metrics patterns

---

## 🛠️ Tools Used

| Tool            | Purpose                                  |
| --------------- | ---------------------------------------- |
| Prometheus      | Time-series metrics collection           |
| Grafana         | Dashboard visualisation                  |
| Spring Actuator | Expose JVM and HTTP metrics from backend |
| Alertmanager    | Alert routing and notification           |
| Claude API      | Anomaly detection and threshold analysis |

---

## 📦 Deliverables

| Deliverable                  | File                                     |
| ---------------------------- | ---------------------------------------- |
| Prometheus Configuration     | `scripts/prometheus.yml`               |
| Monitoring Dashboard Summary | `deliverables/monitoring-dashboard.md` |
![Uploading image.png…]()

---

## 🤖 AI Usage

**Prompt for anomaly detection:**

```
Here are SmartCart API response time metrics over the last 30 minutes during load test.
p50: 45ms, p95: 189ms, p99: 450ms. At minute 22, p99 spiked to 1800ms.
Diagnose the likely root cause and what monitoring alerts should be configured.
```

**AI Analysis:**

- Spike at minute 22 likely indicates GC pause or DB connection pool exhaustion
- Recommend alert: `p99 > 500ms for 2 consecutive minutes`
- Recommend alert: `DB connection pool utilisation > 80%`
- Recommend alert: `JVM heap usage > 85%`
- Suggest adding `/actuator/metrics/hikaricp.connections.active` to dashboard

---

## 📸 Evidence

- `evidence/prometheus-targets.png` — Prometheus showing SmartCart backend as active target
- `evidence/grafana-api-dashboard.png` — Grafana dashboard: API response times during load test
- `evidence/grafana-error-rate.png` — Error rate panel showing 0% during smoke test

---

## ✅ How to Validate This Phase

1. Access Prometheus: http://localhost:9090 → Status → Targets → `smartcart-backend` should be UP
2. Access Grafana: http://localhost:3001 (admin/smartcart2025)
3. Open "SmartCart QA Dashboard" — verify all panels showing data
4. Trigger a load test (Phase 05) and watch metrics update in real-time
