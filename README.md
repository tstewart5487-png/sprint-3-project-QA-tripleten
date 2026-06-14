# 🚗 Urban Routes — QA Project 3

> Manual QA testing project completed as part of the TripleTen QA Engineering program.

---

## 📋 Project Overview

This project covers manual QA testing of two new features in the **Urban Routes** web application:

- 🚁 **Aero Taxi** — A new air taxi service integrated into Urban Routes' Custom mode
- 🏎️ **Carsharing** — A carsharing booking flow with class selection, driver's license verification, and card payment

Testing involved requirements decomposition, equivalence partitioning, boundary value analysis, test case design, and bug reporting.

---

## 🛠️ Tools Used

![Chrome DevTools](https://img.shields.io/badge/Chrome%20DevTools-4285F4?style=flat&logo=googlechrome&logoColor=white)
![Jira](https://img.shields.io/badge/Jira-0052CC?style=flat&logo=jira&logoColor=white)
![GitHub](https://img.shields.io/badge/GitHub-181717?style=flat&logo=github&logoColor=white)
![Google Sheets](https://img.shields.io/badge/Google%20Sheets-34A853?style=flat&logo=googlesheets&logoColor=white)

---

## 🧪 Features Tested

### 🚁 Aero Taxi (FR-AT1 – FR-AT6)
| Requirement | Description |
|-------------|-------------|
| FR-AT1 | Aero Taxi icon displays on transport panel without distorting the interface |
| FR-AT2 | Aero Taxi icon becomes inactive when user changes from "Custom" mode |
| FR-AT3 | Aero Taxi icon becomes active when user selects "Custom" mode |
| FR-AT4 | Total travel time and cost are calculated correctly |
| FR-AT5 | Calculation result displays the service name received from the server |
| FR-AT6 | Calculation result displays total travel time and cost for Aero Taxi |

### 🏎️ Carsharing — Payment Methods (FR-CS32 – FR-CS35)
| Requirement | Description |
|-------------|-------------|
| FR-CS32 | User must enter card information and click "Add" to order a car |
| FR-CS33 | Input field limits applied to card number and CVV/CVC fields |
| FR-CS35 | Card payment details are encrypted when sent from client to server |

---

## 📂 Repository Structure

```
urban-routes-qa-project/
├── README.md
├── requirements/
│   ├── aero-taxi-requirements.md
│   └── carsharing-requirements.md
├── test-cases/
│   └── aero-taxi-test-cases.md
├── equivalence-partitioning/
│   └── card-payment-ep-bva.md
└── bug-reports/
    └── S3-1-aero-taxi-price-error.md
```

---

## 📊 Test Results Summary

| Metric | Value |
|--------|-------|
| Total Test Cases | 4 |
| Passed | 0 |
| Failed | 4 |
| Pass Rate | 0% |

> ⚠️ All 4 test cases failed due to a critical bug (S3-1). The app throws a `TypeError: Cannot read properties of undefined (reading 'price')` when the Aero Taxi feature is enabled via server override, preventing travel time and cost from being calculated or displayed.

---

## 🐛 Bugs Found

| Bug ID | Summary | Severity | Status |
|--------|---------|----------|--------|
| [S3-1](https://tstewart5487qa.atlassian.net/jira/software/projects/S3/boards/35?selectedIssue=S3-1) | App throws TypeError when Aero Taxi JSON override is applied — travel time and cost not displayed | High | Open |

---

## ⚙️ Test Environment

- **Browser:** Chrome Version 149.0.7827.55 (Official Build) (64-bit)
- **Application:** Urban Routes v2.0
- **Testing Type:** Manual — End-to-End

---

*Part of my QA Engineering journey at TripleTen* 🎓
