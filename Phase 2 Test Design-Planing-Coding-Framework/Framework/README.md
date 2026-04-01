# Test Environment Setup

## 🎯 Objective

Set up a fully containerized, reproducible test environment for SmartCart including backend, database, and frontend — enabling consistent test execution across all team members and CI/CD pipelines.

---

## 📋 Tasks Performed

- Configured Docker Compose for full-stack SmartCart environment
- Set up MySQL database with test data seeding scripts
- Configured Spring Boot backend with test profile
- Set up React frontend with environment variables for QA
- Validated all service health checks
- Optionally used AI to generate test data configurations

---

## 🛠️ Tools Used

| Tool                    | Purpose                 |
| ----------------------- | ----------------------- |
| Docker & Docker Compose | Container orchestration |
| MySQL 8.0               | Database                |
| Spring Boot             | Backend API             |
| React + Nginx           | Frontend                |
| Flyway                  | Database migrations     |
| AI (Claude)             | Generate test data sets |

---

## 📦 Deliverables

| Deliverable                  | File                                        |
| ---------------------------- | ------------------------------------------- |
| Environment Setup Guide      | `deliverables/environment-setup-guide.md` |
| Docker Compose Configuration | `scripts/docker-compose.yml`              |
![Uploading image.png…]()

---

## 🤖 AI Usage (Optional)

**Prompt for Test Data Generation:**

```
Generate SQL INSERT statements to seed a SmartCart database with:
- 5 test users (1 admin, 4 regular)
- 20 products across 4 categories
- 3 existing orders in various states (pending, shipped, delivered)
Ensure data covers edge cases: out-of-stock items, max-price items.
```

---

## 📸 Evidence

- `evidence/docker-compose-up.png` — All services running (docker ps output)
- `evidence/swagger-ui.png` — OpenAPI interface showing all SmartCart endpoints
- `evidence/db-schema.png` — Database schema diagram

---

## ✅ How to Run This Phase

```bash
cd phase-04-test-environment-setup/scripts
docker-compose up -d
docker-compose ps   # All services should show "Up"
# Backend: http://localhost:8080/swagger-ui.html
# Frontend: http://localhost:3000
# DB: localhost:3306
```
