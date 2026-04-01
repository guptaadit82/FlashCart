# Test Design

## 🎯 Objective

Create structured test coverage through detailed test cases and a Requirement Traceability Matrix (RTM) to ensure every requirement has corresponding test coverage. AI is used to auto-generate boundary/negative scenarios.

---

## 📋 Tasks Performed

- Designed test cases for all 6 modules using BDD-style and tabular formats
- Created RTM mapping each requirement to one or more test cases
- Used AI to auto-generate boundary value tests and negative scenarios
- Applied equivalence partitioning and boundary value analysis techniques

---

## 🛠️ Tools Used

| Tool          | Purpose                                        |
| ------------- | ---------------------------------------------- |
| JIRA / Xray   | Test case management                           |
| Google Sheets | RTM creation                                   |
| Claude API    | Auto-generate boundary and negative test cases |
| OpenAPI Spec  | Source for API test case generation            |

---

## 📦 Deliverables

| Deliverable                           | File                           |
| ------------------------------------- | ------------------------------ |
| Test Case Sheet                       | `deliverables/test-cases.md` |
| Requirement Traceability Matrix (RTM) | `deliverables/rtm.md`        |
<img width="1207" height="764" alt="image" src="https://github.com/user-attachments/assets/7dde9f0f-4c63-4ef8-9cfd-2ff1f2c26739" />
![Uploading image.png…]()



---

## 🤖 AI Usage

**Prompt for API Test Generation:**

```
Given this OpenAPI spec for POST /api/auth/register with fields:
email (string, required), password (string, min 8 chars), name (string, required)
Generate all positive, negative, boundary, and security test cases.
```

**AI-Generated Negative Cases (sample):**

- Register with SQL injection in email field
- Register with 255-character email
- Register with Unicode password
- Register with missing Content-Type header
- Register with duplicate email (race condition via concurrent calls)
- Register with HTML tags in name field (XSS check)

---

## 📸 Evidence

- `evidence/test-cases-screenshot.png` — Test case sheet as executed in JIRA/Xray
- `evidence/rtm-screenshot.png` — RTM coverage matrix

---

## ✅ How to Validate This Phase

1. Open `deliverables/rtm.md` — every requirement from BRD should map to at least one TC
2. Open `deliverables/test-cases.md` — verify test case IDs match RTM references
3. Check coverage percentage: should be ≥ 95% for critical paths
