# CI/CD Integration

## 🎯 Objective

Integrate the full automation test suite into a CI/CD pipeline using GitHub Actions. Ensure tests run automatically on every pull request and merge, with intelligent retry strategies for flaky tests and optimised parallel execution.

---

## 📋 Tasks Performed

- Configured GitHub Actions workflow for automated test execution
- Created parallel job matrix for API and UI test suites
- Added Allure report publishing to GitHub Pages
- Configured Jenkinsfile for teams using Jenkins
- Used AI to suggest retry strategies for flaky tests and pipeline optimisation

---

## 🛠️ Tools Used

| Tool           | Purpose                                   |
| -------------- | ----------------------------------------- |
| GitHub Actions | Primary CI/CD pipeline                    |
| Jenkins        | Alternative pipeline for enterprise teams |
| Docker         | Containerised test execution              |
| Allure         | Test report publishing                    |
| Claude API     | Flaky test retry strategy suggestions     |

---

## 📦 Deliverables

| Deliverable             | File                                  |
| ----------------------- | ------------------------------------- |
| GitHub Actions Workflow | `.github/workflows/qa-pipeline.yml` |
| Jenkinsfile             | `Jenkinsfile`                       |

---

## 🤖 AI Usage

**Prompt for retry strategy:**

```
Our Selenium tests for SmartCart have ~15% flakiness on CI due to slow page loads.
Suggest a retry strategy that minimises false failures without masking real bugs.
```

**AI Recommendations:**

1. Retry failed tests up to 2 times (not 3 — masks real bugs)
2. Add 2-second delay between retries
3. Capture screenshot + page source on each failure before retry
4. Separate retry count in report (show "Passed on retry 2")
5. Alert if same test flakes > 3 times in 5 builds

---

## 📸 Evidence

- `evidence/github-actions-run.png` — Successful pipeline run in GitHub Actions
- `evidence/pipeline-stages.png` — Pipeline stage breakdown
<img width="571" height="821" alt="image" src="https://github.com/user-attachments/assets/323efe84-d376-44fa-942c-48843691e801" />


---

## ✅ How to Validate This Phase

1. Push a commit to any branch — Actions workflow should trigger
2. Open GitHub Actions tab → verify all jobs complete
3. Check Allure report is published to GitHub Pages
4. For Jenkins: `Build Now` → verify stage view shows all stages passing
