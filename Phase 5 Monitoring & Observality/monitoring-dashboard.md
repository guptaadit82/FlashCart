# Monitoring Dashboards & Metrics Report
## SmartCart QA Ecosystem — Phase 08

---

## Dashboard Overview

Three Grafana dashboards were configured for SmartCart QA Monitoring:

| Dashboard | Purpose | Key Panels |
|-----------|---------|------------|
| **SmartCart API Performance** | API response times, throughput, error rates | p50/p95/p99 latency, RPS, HTTP error % |
| **SmartCart JVM Health** | JVM memory, GC, threads | Heap usage, GC pause time, thread count |
| **SmartCart Load Test Monitor** | Real-time monitoring during k6 tests | VU count, request rate, failure rate |

---

## Key Metrics & PromQL Queries

### API Response Time (p95)
```promql
histogram_quantile(0.95,
  sum(rate(http_server_requests_seconds_bucket{
    application="smartcart",
    uri!~".*actuator.*"
  }[5m])) by (le, uri)
)
```

### HTTP Error Rate
```promql
sum(rate(http_server_requests_seconds_count{
  application="smartcart",
  status=~"5.."
}[5m]))
/
sum(rate(http_server_requests_seconds_count{
  application="smartcart"
}[5m])) * 100
```

### Requests Per Second
```promql
sum(rate(http_server_requests_seconds_count{
  application="smartcart"
}[1m]))
```

### JVM Heap Usage
```promql
jvm_memory_used_bytes{area="heap", application="smartcart"}
/
jvm_memory_max_bytes{area="heap", application="smartcart"} * 100
```

### DB Connection Pool Usage
```promql
hikaricp_connections_active{application="smartcart"}
/
hikaricp_connections_max{application="smartcart"} * 100
```

---

## Alert Rules

### API Alerts (`alerts/api_alerts.yml`)

```yaml
groups:
  - name: smartcart-api-alerts
    rules:

      - alert: HighResponseTime
        expr: |
          histogram_quantile(0.95,
            sum(rate(http_server_requests_seconds_bucket[5m])) by (le)
          ) > 0.2
        for: 2m
        labels:
          severity: warning
          team: qa
        annotations:
          summary: "SmartCart API p95 response time exceeds 200ms"
          description: "p95 response time is {{ $value | humanizeDuration }}"

      - alert: HighErrorRate
        expr: |
          sum(rate(http_server_requests_seconds_count{status=~"5.."}[5m]))
          /
          sum(rate(http_server_requests_seconds_count[5m])) > 0.01
        for: 1m
        labels:
          severity: critical
          team: qa
        annotations:
          summary: "SmartCart error rate exceeds 1%"
          description: "Error rate is {{ $value | humanizePercentage }}"

      - alert: APIDown
        expr: up{job="smartcart-backend"} == 0
        for: 30s
        labels:
          severity: critical
        annotations:
          summary: "SmartCart backend is DOWN"
```

### JVM Alerts (`alerts/jvm_alerts.yml`)

```yaml
groups:
  - name: smartcart-jvm-alerts
    rules:

      - alert: HighJvmHeapUsage
        expr: |
          jvm_memory_used_bytes{area="heap"}
          /
          jvm_memory_max_bytes{area="heap"} > 0.85
        for: 5m
        labels:
          severity: warning
        annotations:
          summary: "JVM heap usage above 85%"

      - alert: HighGCTime
        expr: |
          rate(jvm_gc_pause_seconds_sum[5m]) > 0.1
        for: 5m
        labels:
          severity: warning
        annotations:
          summary: "GC pause time exceeds 100ms/s — possible memory pressure"
```

---

## Performance Metrics During Load Test (Evidence)

The following metrics were captured during the k6 load test execution (100 VUs, 5-minute run):

| Metric | Target | Observed | Status |
|--------|--------|----------|--------|
| API p95 Response Time | < 200ms | 187ms | ✅ PASS |
| API p99 Response Time | < 500ms | 423ms | ✅ PASS |
| HTTP Error Rate | < 1% | 0.3% | ✅ PASS |
| Requests Per Second | > 50 RPS | 78 RPS | ✅ PASS |
| JVM Heap Usage (peak) | < 85% | 72% | ✅ PASS |
| DB Connection Pool | < 80% | 65% | ✅ PASS |

**Stress Test (500 VUs):**

| Metric | Target | Observed | Status |
|--------|--------|----------|--------|
| API p95 Response Time | < 500ms | 489ms | ✅ PASS |
| HTTP Error Rate | < 5% | 1.8% | ✅ PASS |
| System Recovery Time | < 60s | 45s | ✅ PASS |

---

## AI-Assisted Anomaly Detection

During stress testing, the AI was asked to analyse metric patterns. Claude identified:

1. **Minute 22 spike (p99: 1800ms)** — Identified as GC pause from old-gen collection. Recommendation: increase heap size from 512MB to 1GB.
2. **DB connection pool saturation at 490 VUs** — Recommend increasing pool max from 10 to 20 connections.
3. **Recommendation**: Add circuit breaker (Resilience4j) to payment service to prevent cascade failures under stress.

---

*Grafana dashboard JSON exports stored in `scripts/grafana/dashboards/`. Import via Grafana UI → Dashboards → Import.*
