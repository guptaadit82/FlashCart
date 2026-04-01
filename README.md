# 🛒 SmartCart QA Ecosystem — Master Repository

> **A complete STLC-driven, AI-augmented QA framework for the SmartCart e-commerce platform**

---

## 📌 Project Overview

The **SmartCart QA Ecosystem** is a comprehensive Quality Assurance framework built around the Software Testing Life Cycle (STLC), integrated with modern SDET practices and AI/LLM augmentation at every phase. It covers everything from Requirement Engineering to Final Delivery — making this a reference-grade QA portfolio project.

The underlying system under test is **SmartCart**, an e-commerce platform offering:
- User Authentication (Register / Login / JWT)
- Product Catalog (Browse, Search, Filter)
- Cart Management (Add, Remove, Update)
- Checkout & Order Processing
- Payment Gateway Integration
- Admin Dashboard

---

## 🏗️ Architecture Diagram

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                        SmartCart QA Ecosystem                               │
│                                                                             │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐  ┌───────────────┐  │
│  │ Phase 01     │  │ Phase 02     │  │ Phase 03     │  │ Phase 04      │  │
│  │ Requirement  │→ │ Test         │→ │ Test         │→ │ Environment   │  │
│  │ Engineering  │  │ Planning     │  │ Design       │  │ Setup         │  │
│  └──────────────┘  └──────────────┘  └──────────────┘  └───────────────┘  │
│         ↓                                                        ↓          │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐  ┌───────────────┐  │
│  │ Phase 09     │  │ Phase 08     │  │ Phase 07     │  │ Phase 05      │  │
│  │ Test         │← │ Observability│← │ CI/CD        │← │ Test          │  │
│  │ Closure      │  │ & Monitoring │  │ Integration  │  │ Execution     │  │
│  └──────────────┘  └──────────────┘  └──────────────┘  └───────────────┘  │
│         ↓                                                        ↓          │
│  ┌──────────────────────────────────────────────────────────────────────┐   │
│  │         Phase 10: Final Codebase Delivery & Documentation             │   │
│  └──────────────────────────────────────────────────────────────────────┘   │
│                              Phase 06: Defect Management (continuous)        │
└─────────────────────────────────────────────────────────────────────────────┘
```

---

## 🔄 End-to-End Workflow (STLC + SDET + AI Integration)

```
Requirements → AI Edge Case Generation
     ↓
Test Planning → AI Risk-Based Prioritization
     ↓
Test Design (Test Cases + RTM) → AI Auto-generation from API Specs
     ↓
Environment Setup (Docker + DB + Backend + Frontend)
     ↓
Test Execution:
  ├── Manual Testing
  ├── UI Automation (Selenium/Playwright)
  ├── API Automation (Rest Assured / Karate)
  └── Performance Testing (JMeter / k6)
     ↓
Defect Management → AI Defect Summarization & Grouping
     ↓
CI/CD Pipeline (GitHub Actions / Jenkins)
     ↓
Observability (Prometheus + Grafana + Dynatrace)
     ↓
Test Closure Report → AI Quality Trend Insights
```

---

## 🧰 Tech Stack

| Layer | Tools |
|-------|-------|
| **Backend** | Spring Boot / Node.js |
| **Frontend** | React.js |
| **Database** | MySQL / PostgreSQL |
| **Containerization** | Docker, Docker Compose |
| **UI Automation** | Selenium WebDriver, Playwright |
| **API Automation** | Rest Assured, Karate Framework |
| **Performance** | Apache JMeter, k6 |
| **CI/CD** | GitHub Actions, Jenkins |
| **Monitoring** | Prometheus, Grafana, Dynatrace |
| **AI/LLM** | Claude API (Anthropic), ChatGPT |
| **Test Management** | JIRA, TestRail |
| **Version Control** | Git, GitHub |
| **Reporting** | Allure Reports, ExtentReports |

---

## 📂 Repository Structure

```
smartcart-qa-ecosystem/
│
├── README.md                              ← You are here (Master README)
│
├── phase-01-requirement-engineering/
│   ├── README.md
│   ├── deliverables/
│   │   ├── BRD.md
│   │   └── user-stories.md
│   └── evidence/
│
├── phase-02-test-planning/
│   ├── README.md
│   ├── deliverables/
│   │   └── test-plan.md
│   └── evidence/
│
├── phase-03-test-design/
│   ├── README.md
│   ├── deliverables/
│   │   ├── test-cases.md
│   │   └── rtm.md
│   └── evidence/
│
├── phase-04-test-environment-setup/
│   ├── README.md
│   ├── deliverables/
│   │   └── environment-setup-guide.md
│   ├── scripts/
│   │   └── docker-compose.yml
│   └── evidence/
│
├── phase-05-test-execution/
│   ├── README.md
│   ├── scripts/
│   │   ├── ui-automation/
│   │   ├── api-automation/
│   │   └── performance/
│   ├── reports/
│   └── evidence/
│
├── phase-06-defect-management/
│   ├── README.md
│   ├── deliverables/
│   │   └── bug-reports.md
│   └── evidence/
│
├── phase-07-cicd-integration/
│   ├── README.md
│   ├── .github/workflows/
│   │   └── qa-pipeline.yml
│   ├── Jenkinsfile
│   └── evidence/
│
├── phase-08-observability-monitoring/
│   ├── README.md
│   ├── scripts/
│   │   └── prometheus.yml
│   ├── deliverables/
│   │   └── monitoring-dashboard.md
│   └── evidence/
│
├── phase-09-test-closure/
│   ├── README.md
│   ├── deliverables/
│   │   └── test-closure-report.md
│   └── evidence/
│
└── phase-10-final-delivery/
    ├── README.md
    └── deliverables/
        └── project-summary.md
```

---

## 🚀 How to Run the Full Project

### Prerequisites
- Java 17+, Node.js 18+, Maven 3.8+
- Docker & Docker Compose
- Python 3.10+ (for AI scripts)

### Step 1 — Clone the Repository
```bash
git clone https://github.com/guptaadit82/smartcart-project.git
cd smartcart-project
```

### Step 2 — Start the Environment
```bash
cd phase-04-test-environment-setup/scripts
docker-compose up -d
```

### Step 3 — Run API Automation
```bash
cd phase-05-test-execution/scripts/api-automation
mvn test -Dsuite=regression
```

### Step 4 — Run UI Automation
```bash
cd phase-05-test-execution/scripts/ui-automation
mvn test -Dbrowser=chrome -Dsuite=smoke
```

### Step 5 — Run Performance Tests
```bash
cd phase-05-test-execution/scripts/performance
jmeter -n -t SmartCart_PerfTest.jmx -l results.jtl -e -o reports/
```

### Step 6 — View Reports
Open `phase-05-test-execution/reports/allure-report/index.html` in a browser.

---

## 👤 Author

**Adit Gupta** | Senior SDET  
GitHub: [@guptaadit82](https://github.com/guptaadit82)

---

## 📜 License

MIT License — see [LICENSE](./LICENSE) for details.
