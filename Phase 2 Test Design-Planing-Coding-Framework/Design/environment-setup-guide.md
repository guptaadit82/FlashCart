# Environment Setup Guide
## SmartCart QA Ecosystem — Phase 04

---

## Prerequisites

| Tool | Version | Installation |
|------|---------|-------------|
| Docker | 24.0+ | https://docs.docker.com/get-docker/ |
| Docker Compose | 2.20+ | Bundled with Docker Desktop |
| Java | 17+ | https://adoptium.net/ |
| Maven | 3.8+ | https://maven.apache.org/ |
| Node.js | 18+ | https://nodejs.org/ |
| Git | 2.x | https://git-scm.com/ |

---

## Step 1 — Clone Repository

```bash
git clone https://github.com/guptaadit82/smartcart-project.git
cd smartcart-project/phase-04-test-environment-setup/scripts
```

---

## Step 2 — Start All Services

```bash
docker-compose up -d
```

This starts:
- MySQL 8.0 (port 3306)
- Spring Boot Backend (port 8080)
- React Frontend via Nginx (port 3000)
- Prometheus (port 9090)
- Grafana (port 3001)
- Selenium Grid Hub (port 4444)
- Chrome + Firefox Selenium Nodes

---

## Step 3 — Verify Services

```bash
docker-compose ps
```

Expected output — all containers with status `Up`:
```
NAME                       STATUS
smartcart-mysql            Up (healthy)
smartcart-backend          Up (healthy)
smartcart-frontend         Up
smartcart-prometheus       Up
smartcart-grafana          Up
smartcart-selenium-hub     Up
smartcart-chrome-node      Up
smartcart-firefox-node     Up
```

---

## Step 4 — Validate Endpoints

| Service | URL | Expected |
|---------|-----|----------|
| Backend Health | http://localhost:8080/actuator/health | `{"status":"UP"}` |
| Swagger UI | http://localhost:8080/swagger-ui.html | OpenAPI documentation |
| Frontend | http://localhost:3000 | SmartCart login page |
| Selenium Grid | http://localhost:4444/ui | Grid console showing nodes |
| Prometheus | http://localhost:9090 | Prometheus query UI |
| Grafana | http://localhost:3001 | Login (admin/smartcart2025) |

---

## Step 5 — Seed Test Data

```bash
# Connect to MySQL and run seed script
docker exec -i smartcart-mysql mysql -u qauser -pqapassword smartcart_qa < init-db/seed-data.sql
```

### Seed Data Includes:
- **Users:** 5 users (1 admin: admin@smartcart.com / Admin@2025!)
- **Products:** 20 products across 4 categories (Electronics, Clothing, Books, Home)
- **Orders:** 3 historical orders in states: PENDING, SHIPPED, DELIVERED
- **Edge case data:** 1 out-of-stock product, 1 maximum-price product (₹4,99,999)

---

## Step 6 — Test Database Connectivity

```bash
docker exec -it smartcart-mysql mysql -u qauser -pqapassword -e "USE smartcart_qa; SHOW TABLES;"
```

Expected tables:
```
users, products, categories, cart_items, orders, order_items, payments, addresses
```

---

## Teardown

```bash
# Stop all services
docker-compose down

# Stop and remove volumes (clean slate)
docker-compose down -v
```

---

## Troubleshooting

| Issue | Fix |
|-------|-----|
| Backend fails to connect to DB | Wait 30s for MySQL healthcheck; retry `docker-compose restart backend` |
| Port conflict on 8080 | Change port mapping in docker-compose.yml |
| Selenium node not registering | Restart node: `docker-compose restart selenium-chrome` |
| Grafana blank dashboards | Import dashboards from `grafana/provisioning/dashboards/` |
