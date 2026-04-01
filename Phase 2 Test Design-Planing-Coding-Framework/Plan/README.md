# Test Planning

## 🎯 Objective

Define the complete testing strategy, scope, tools, resource allocation, timelines, and risk mitigation plan for the SmartCart QA Ecosystem.

---

## 📋 Tasks Performed

- Analyzed BRD and user stories from Phase 01
- Defined testing scope (in-scope and out-of-scope modules)
- Selected test types: Functional, Regression, API, UI, Performance, Security
- Identified risks and mitigation strategies
- Leveraged AI to suggest risk-based test prioritization

---

## 🛠️ Tools Used

| Tool                  | Purpose                                    |
| --------------------- | ------------------------------------------ |
| Confluence / Markdown | Test Plan documentation                    |
| JIRA                  | Test tracking and sprint management        |
| Claude API            | Risk-based test prioritization suggestions |
| Excel / Google Sheets | Timeline and effort estimation             |

---

## 📦 Deliverables

| Deliverable        | File                          |
| ------------------ | ----------------------------- |
| Test Plan Document | `deliverables/test-plan.md` |
<img width="1122" height="787" alt="image" src="https://github.com/user-attachments/assets/1fdde48e-41fb-4a2a-97d1-ac3a5fd0508e" />
<img width="1159" height="748" alt="image" src="https://github.com/user-attachments/assets/cc402cee-1e09-48db-9109-8dde0cb0d3a0" />

---

## 🤖 AI Usage

**Prompt for Risk-Based Prioritization:**

```
Given these SmartCart modules: Authentication, Product Catalog, Cart, 
Checkout, Payment, Admin Dashboard — rank them by testing risk based on 
business impact, complexity, and defect probability. Suggest test prioritization.
```

**AI Output (summarized):**

1. **Payment** — Highest risk (financial impact, 3rd-party integration)
2. **Authentication** — High risk (security, JWT vulnerabilities)
3. **Cart Management** — High risk (concurrent access, data integrity)
4. **Checkout** — Medium-High risk (data flow complexity)
5. **Product Catalog** — Medium risk (read-heavy, lower mutation risk)
6. **Admin Dashboard** — Medium risk (authorization-critical)

---

## 📸 Evidence

- `evidence/test-plan-screenshot.png` — Test Plan document snapshot
- `evidence/sprint-planning-screenshot.png` — JIRA sprint board during planning

---

## ✅ How to Validate This Phase

1. Open `deliverables/test-plan.md`
2. Confirm all SmartCart modules are listed under scope
3. Verify risk register has mitigations for each risk
4. Cross-check tool list against Phase 05 execution tools
