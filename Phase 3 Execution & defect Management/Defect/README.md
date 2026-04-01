# Defect Management

## 🎯 Objective

Track, manage, and analyse all defects discovered during test execution. Use AI to auto-summarise defect clusters and group similar issues to surface systemic root causes.

---

## 📋 Tasks Performed

- Logged all defects found during Phase 05 execution into JIRA
- Classified each defect by severity, priority, and module
- Performed root cause analysis (RCA) for Critical/High defects
- Used AI to group similar defects and identify patterns
- Tracked defect lifecycle from Open → In Progress → Fixed → Verified → Closed

---

## 🛠️ Tools Used

| Tool           | Purpose                                           |
| -------------- | ------------------------------------------------- |
| JIRA           | Defect tracking and lifecycle management          |
| Claude API     | Auto-summarise defect clusters, identify patterns |
| Allure Reports | Defect-linked test execution evidence             |
| Confluence     | RCA documentation                                 |

---

## 📦 Deliverables

| Deliverable                                | File                            |
| ------------------------------------------ | ------------------------------- |
| Bug Reports (with severity, priority, RCA) | `deliverables/bug-reports.md` |
<img width="1112" height="786" alt="image" src="https://github.com/user-attachments/assets/c34d9319-9855-40c2-a20e-e8b253e582b0" />
<img width="1120" height="756" alt="image" src="https://github.com/user-attachments/assets/e897c032-5f68-41ce-8893-8e46098a51ba" />


---

## 🤖 AI Usage

**Prompt for defect grouping:**

```
Here are 15 defects found during SmartCart testing. 
Group them by root cause category and identify the top 3 systemic issues.
[defect list pasted]
```

**AI-Identified Systemic Issues:**

1. **Missing server-side validation** — 5 defects related to client-only validation
2. **Race conditions in stock management** — 3 defects around concurrent cart operations
3. **JWT expiry edge cases** — 2 defects around token boundary handling

---

## 📸 Evidence

- `evidence/jira-defect-board.png` — JIRA Kanban board showing defect states
- `evidence/defect-metrics.png` — Defect burn-down chart by sprint

---

## ✅ How to Validate This Phase

1. Open `deliverables/bug-reports.md` — each defect should have: ID, title, severity, priority, steps to reproduce, expected vs actual, RCA
2. Verify all Critical/High defects are Closed before release
3. Check defect density: total defects / total test cases executed
