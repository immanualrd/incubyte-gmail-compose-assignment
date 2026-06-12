# Gmail Compose — QA Test Suite

**Repository:** `incubyte-gmail-compose-assignment`
**Assignment:** Test the Gmail *Compose* function — sending an email with subject `Incubyte` and body `QA test for Incubyte`.
**Prepared by:** Immanual Daniel — QA Engineer

---

## Overview

This repository contains a comprehensive manual test suite for the **Gmail Compose & Send** workflow. The suite is delivered as a single Excel workbook with three sheets, covering both **traditional** and **BDD (Gherkin)** styles, with a balanced mix of **positive** and **negative** cases.

| Deliverable | File |
|---|---|
| Test Suite (Excel) | `Gmail_Compose_TestCases_Incubyte_v2.xlsx` |

---

## Coverage at a Glance

| Metric | Count |
|---|---|
| Traditional test cases | 55 |
| BDD scenarios | 24 |
| **Total** | **79** |
| Positive cases | 53 |
| Negative cases | 26 |

---

## Workbook Structure

The Excel file contains three sheets:

### 1. `Traditional Test Cases`
Classic tabular format with columns:
`TC ID | Test Title | Module | Preconditions | Test Steps | Test Data | Expected Result | Type | Priority | Status`

Organized into logical sections: Compose Window, To Field, Subject, Body, CC/BCC, Attachments, Draft, Send, Keyboard Shortcuts, UI/UX, Security, and Regression.

### 2. `BDD Test Cases`
Behaviour-Driven format using **Given / When / Then** (Gherkin):
`Scenario ID | Feature | Scenario Title | Given | When | Then | Type`

### 3. `Summary`
Suite metrics, coverage map by area, priority key, and a colour legend.

---

## Legend

| Colour | Meaning |
|---|---|
| Green | Positive test case |
| Red | Negative test case |
| Blue | BDD scenario |

**Priority levels:**
- **P1** — Critical: must pass before any release gate
- **P2** — High: tested every cycle
- **P3** — Coverage: tested when time permits

---

## Test Design Approach

The suite goes beyond the happy path to reflect real-world QA depth:

- **Functional happy path** — open compose, fill To/Subject/Body, send, verify in Sent folder
- **Field-level validation** — empty recipient, invalid email format, empty subject confirmation
- **CC / BCC** — visibility rules and validation
- **Attachments** — valid files, multiple files, size-limit (25MB) and `.exe` blocking
- **Draft & recovery** — auto-save, resume, discard, tab-close and refresh recovery
- **Keyboard shortcuts** — `C` to compose, `Ctrl+Enter` to send, `Esc` to close
- **Security** — XSS (subject & body), SQL/HTML injection, executable blocking
- **Network / offline** — graceful queueing and send-on-reconnect
- **UI / UX & accessibility** — responsive mobile layout, tab navigation, spell check
- **Localization** — non-English (Unicode) subject and body
- **Regression** — ad-blocker compatibility, multiple compose windows, refresh recovery

---

## Classification Note

Classification follows a consistent principle: **BDD scenarios are typed by the behaviour being validated** (e.g. successful draft recovery  Positive), while **traditional cases triggered by abnormal conditions are treated as Negative / error-handling**. This keeps the BDD layer behaviour-focused and the traditional layer condition-focused.

---

## Test Design Techniques

This suite applies established test design techniques to maximize coverage and minimize redundancy:

- **Equivalence Partitioning** — grouping valid/invalid inputs (e.g. email formats) into classes
- **Boundary Value Analysis** — testing limits such as the 25MB attachment cap and 998-character subject
- **Error Guessing** — anticipating likely failure points (invalid domains, abrupt tab close)
- **Exploratory Testing** — uncovering issues outside scripted paths
- **Positive Testing** — validating expected, correct behaviour
- **Negative Testing** — verifying graceful handling of invalid inputs and error states
- **Risk-Based Testing** — prioritizing critical flows (send, validation, security) as P1

---

## How to Use

1. Open `Gmail_Compose_TestCases_Incubyte_v2.xlsx`.
2. Start with the `Summary` sheet for scope and counts.
3. Execute cases from the `Traditional Test Cases` sheet, updating the **Status** column (`Pass` / `Fail` / `Not Run`).
4. Use the `BDD Test Cases` sheet for behaviour-driven execution or automation reference.

---

## Environment

- **Application under test:** Gmail (web)
- **Browsers:** Chrome / latest evergreen browsers
- **Test type:** Manual, functional + non-functional

---

## Author

**Immanual Daniel**
QA Engineer
immanualrd@gmail.com
