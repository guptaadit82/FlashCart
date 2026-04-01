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
| Selenium WebDriver 4.x | UI automation (Chrome, Firefox)     |
| Playwright 1.40+       | UI automation (additional coverage) |
| Rest Assured 5.3.x     | API automation (Java-based)         |
| Karate Framework 1.4.x | API automation (BDD-style)          |
| Apache JMeter 5.6.x    | Load and stress performance testing |
| k6                     | Lightweight performance scripting   |
| Allure Reports         | Unified test reporting              |
| Claude API             | Debug flaky test failures           |

---

## 📦 Deliverables

| Deliverable              | Location                    |
| ------------------------ | --------------------------- |
| UI Automation Scripts    | `scripts/ui-automation/`  |
| API Automation Scripts   | `scripts/api-automation/` |
| Performance Test Scripts | `scripts/performance/`    |
| Execution Reports        | `reports/`                |

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
- `evidence/api-automation-restassured.png` — Rest Assured test run output
- `evidence/ui-selenium-run.png` — Selenium test execution log
- `evidence/jmeter-load-test.png` — JMeter load test summary report
- `evidence/prometheus-metrics.png` — Prometheus metrics during load test
- `evidence/grafana-dashboard.png` — Grafana monitoring dashboard

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
