# Phase 01 — Requirement Engineering

## 🎯 Objective

Analyze SmartCart system features, define user journeys, and establish the full requirements baseline from which all subsequent testing phases derive their scope and coverage.

---

## 📋 Tasks Performed

- Reviewed product backlog and feature specifications for SmartCart
- Conducted stakeholder interviews to capture business needs
- Defined end-to-end user journeys across all major modules
- Leveraged AI (Claude/ChatGPT) to identify missing scenarios and generate edge cases
- Documented acceptance criteria for each user story

---

## 🛠️ Tools Used

| Tool | Purpose |
|------|---------|
| JIRA | User story management |
| Confluence | BRD documentation |
| Claude API | Edge case generation, gap analysis |
| Miro | Journey mapping |

---

## 📦 Deliverables

| Deliverable | File |
|-------------|------|
| Business Requirement Document (BRD) | `deliverables/BRD.md` |
| User Stories with Acceptance Criteria | `deliverables/user-stories.md` |

---

## 🤖 AI Usage

**Prompt used for edge case generation:**
```
Given the SmartCart user journey for "Add to Cart" → "Checkout" → "Payment",
identify all edge cases including boundary conditions, network failures,
concurrent user scenarios, and data validation failures.
```

**AI-Generated Edge Cases (sample):**
- Add item when stock is exactly 1 and two users attempt simultaneously
- Checkout with expired payment card
- Cart total exceeding payment gateway limit (₹5,00,000)
- User session timeout mid-checkout
- Product price change between cart add and checkout
- Invalid coupon code with special characters
- Empty cart checkout attempt
- Negative quantity input in cart

---

## 📸 Evidence

| Screenshot | Description |
|------------|-------------|
| `evidence/brd-screenshot.png` | Business Requirement Document as created |
| `evidence/user-stories-screenshot.png` | User stories in JIRA with acceptance criteria |

*Evidence screenshots collected during actual project execution are stored in the `evidence/` folder.*

---

## ✅ How to Validate This Phase

1. Open `deliverables/BRD.md` — verify all SmartCart modules are covered
2. Open `deliverables/user-stories.md` — verify each story has Given/When/Then acceptance criteria
3. Cross-reference user stories against Phase 03 RTM to confirm full traceability
