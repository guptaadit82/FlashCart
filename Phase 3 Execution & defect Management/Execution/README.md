# Test Execution

## 🎯 Objective

Execute all planned test cases across manual, UI automation, API automation, and performance testing layers. Capture execution logs, Allure reports, and performance metrics as evidence.

---

## 📋 Tasks Performed

- Manual testing of critical user journeys
- UI automation using Selenium WebDriver (cross-browser)
- API automation using Rest Assured and Karate Framework
- Performance testing using Apache JMeter and k6
- AI-assisted debugging of flaky tests and runtime failures

---

## 🛠️ Tools Used

| Tool                   | Purpose                             |
| ---------------------- | ----------------------------------- |
| Cypress 4.x | UI automation (Chrome, Firefox)     |
| Playwright 1.40+       | UI automation (additional coverage) |
| Rest Assured 5.3.x     | API automation (Java-based)         |
| Karate Framework 1.4.x | API automation (BDD-style)          |
| Apache JMeter 5.6.x    | Load and stress performance testing |
| JMETER                   | Lightweight performance scripting   |
| Allure Reports         | Unified test reporting              |
| Claude API             | Debug flaky test failures           |
 | Python                | AI/LLM Testing                      |
---

## 📦 Deliverables

| Deliverable              | Location                    |
| ------------------------ | --------------------------- |
| UI Automation Scripts    | `scripts/ui-automation/`  |
| API Automation Scripts   | `scripts/api-automation/` |
| Performance Test Scripts | `scripts/performance/`    |
| Execution Reports        | `reports/`                |
|Py test                   | `reports`                   | 

---

## 🤖 AI Usage

**Prompt for Debugging Flaky Test:**

```
This Selenium test intermittently fails at step: click on "Add to Cart" button.
Error: ElementClickInterceptedException. The element is rendered but click fails.
What are the possible root causes and fixes?
```

**AI Suggestions:**

1. Add `WebDriverWait` for element to be clickable (not just visible)
2. Scroll element into view before clicking
3. Use JavaScript executor click as fallback
4. Check for overlay/spinner blocking the element

---

## 📸 Evidence

- `evidence/api-automation-karate.png` — Karate test execution results
<img width="698" height="379" alt="image" src="https://github.com/user-attachments/assets/fee53def-1536-4172-9de7-7d5d65109e9c" />
<img width="698" height="318" alt="image" src="https://github.com/user-attachments/assets/27611541-0458-4c8c-a3da-a3e0e3d4c592" />


- `evidence/api-automation-restassured.png` — Rest Assured test run output
<img width="698" height="433" alt="image" src="https://github.com/user-attachments/assets/d9abd04c-dc64-4af9-a39c-b7e9fb0c9cc3" />
<img width="698" height="433" alt="image" src="https://github.com/user-attachments/assets/9474fda6-e610-4441-8987-fff0496ae208" />
<img width="698" height="380" alt="image" src="https://github.com/user-attachments/assets/a52e760a-4019-44cd-bb6d-673c48995d72" />


- `evidence/ui-selenium-run.png` — cypress test execution log
<img width="698" height="437" alt="image" src="https://github.com/user-attachments/assets/e61835b9-6e15-4a9c-85b5-8c1af396e6e9" />
<img width="698" height="317" alt="image" src="https://github.com/user-attachments/assets/ec924cb1-9310-4f21-af34-22460d67aa02" />


- `evidence/jmeter-load-test.png` — JMeter load test summary report
<img width="698" height="214" alt="image" src="https://github.com/user-attachments/assets/b3c9d851-9e9f-4388-9dc6-7f855005947a" />

<img width="698" height="210" alt="image" src="https://github.com/user-attachments/assets/df3fd55c-2136-4ab0-a647-3dd0bc4b0f87" />

<img width="523" height="289" alt="image" src="https://github.com/user-attachments/assets/96b7af8d-ac4a-49c6-9f83-b9501d47d706" />
<img width="698" height="375" alt="image" src="https://github.com/user-attachments/assets/c76e1618-e785-4e21-b8b0-f2626deafff1" />
`evidence/AI/LLM/Testing/pytest/png`-pyest and reports
<img width="698" height="265" alt="image" src="https://github.com/user-attachments/assets/822c4140-d1cd-4116-9226-2e8545dde319" />
<img width="698" height="348" alt="image" src="https://github.com/user-attachments/assets/39a35733-6ea9-4bdd-9978-3559715731fd" />

- `evidence/prometheus-metrics.png` — Prometheus metrics during load test
<img width="698" height="230" alt="image" src="https://github.com/user-attachments/assets/adaf4392-33ed-4656-b657-5a6191b7cd4b" />

- `evidence/grafana-dashboard.png` — Grafana monitoring dashboard
<img width="698" height="336" alt="image" src="https://github.com/user-attachments/assets/690e3fe9-d7d6-400e-a05c-6b24c0be61e8" />
![Uploading image.png…]()

---

## ✅ How to Run

### API Automation (Rest Assured)

```bash
cd scripts/api-automation/rest-assured
mvn test -Dsuite=regression -Denv=qa
# Report: target/allure-results → allure serve
```

### API Automation (Karate)

```bash
cd scripts/api-automation/karate
mvn test -Dkarate.env=qa
# Report: target/karate-reports/karate-summary.html
```

### UI Automation (Selenium)

```bash
cd scripts/ui-automation
mvn test -Dbrowser=chrome -Dsuite=smoke -Denv=qa
# Selenium Grid must be running (Phase 04)
```

### Performance Tests (JMeter)

```bash
cd scripts/performance
jmeter -n -t SmartCart_LoadTest.jmx -l results/results.jtl -e -o reports/
```

### Performance Tests (k6)

```bash
cd scripts/performance
k6 run smartcart-load.js
```
