# 🚁 Aero Taxi — Test Cases

> Test cases for FR-AT4 and FR-AT6 of the Urban Routes Aero Taxi feature.

---

## ⚙️ Setup: Enabling Aero Taxi

The Aero Taxi feature is not enabled by default. Follow these steps before running any test:

1. Open **Chrome DevTools** (`F12`)
2. Navigate to the **Network** panel
3. Search for `types` in the search field
4. Right-click the `types` JSON file and select **Override content**
5. Paste the following JSON over the existing content:

```json
[{"id":"car","name":"Car","icons":{"inactive":"car.svg","active":"car-active.svg"}},{"id":"walk","name":"Walk","icons":{"inactive":"walk.svg","active":"walk-active.svg"}},{"id":"taxi","name":"Taxi","icons":{"inactive":"taxi.svg","active":"taxi-active.svg"}},{"id":"bike","name":"Bike","icons":{"inactive":"bike.svg","active":"bike-active.svg"}},{"id":"scooter","name":"Scooter","icons":{"inactive":"scooter.svg","active":"scooter-active.svg"}},{"id":"drive","name":"Drive","icons":{"inactive":"car.svg","active":"car-active.svg"}},{"id":"aero","name":"Air taxi","icons":{"inactive":"helicopter.svg","active":"helicopter-active.svg"}}]
```

6. Save with `Ctrl+S` (Windows) or `Cmd+S` (Mac)
7. Reload the page

---

## 🧪 Test Cases

| ID | Test Case | Precondition | Steps | Test Technique | Test Data | Expected Result | Environment | Actual Result | Status | Bug ID |
|----|-----------|--------------|-------|----------------|-----------|-----------------|-------------|---------------|--------|--------|
| t-1 | The system should display the total travel time correctly | Server is running. DevTools is open. | 1. Navigate to the Network panel in DevTools 2. Search "types" in the search field 3. Override the default JSON with the Aero Taxi JSON 4. Save and reload the page 5. Enter "East" in the From field 6. Enter "1300" in the To field 7. Select "Custom" mode 8. Click the Aero Taxi icon 9. Observe the calculation result | End-to-End | From: `East` To: `1300` | The system displays the total travel time correctly | Chrome 149.0.7827.55 (64-bit) | Page goes blank. No total travel time is displayed. App throws `TypeError: Cannot read properties of undefined (reading 'price')` | ❌ Fail | [S3-1](https://tstewart5487qa.atlassian.net/jira/software/projects/S3/boards/35?selectedIssue=S3-1) |
| t-2 | The system should display the total travel cost correctly | Server is running. DevTools is open. | 1. Navigate to the Network panel in DevTools 2. Search "types" in the search field 3. Override the default JSON with the Aero Taxi JSON 4. Save and reload the page 5. Enter "East" in the From field 6. Enter "1300" in the To field 7. Select "Custom" mode 8. Click the Aero Taxi icon 9. Observe the calculation result | End-to-End | From: `East` To: `1300` | The system displays the total travel cost correctly | Chrome 149.0.7827.55 (64-bit) | Page goes blank. No total travel cost is displayed. App throws `TypeError: Cannot read properties of undefined (reading 'price')` | ❌ Fail | [S3-1](https://tstewart5487qa.atlassian.net/jira/software/projects/S3/boards/35?selectedIssue=S3-1) |
| t-3 | The system should not display travel time when no addresses are entered | Server is running. DevTools is open. Aero Taxi enabled via server override. | 1. Select "Custom" mode 2. Click the Aero Taxi icon 3. Leave the From and To fields empty 4. Observe the result | End-to-End | From: ` ` To: ` ` | No travel time is displayed | Chrome 149.0.7827.55 (64-bit) | The system does not display any travel time | ❌ Fail | |
| t-4 | The system should not display travel cost when no addresses are entered | Server is running. DevTools is open. Aero Taxi enabled via server override. | 1. Select "Custom" mode 2. Click the Aero Taxi icon 3. Leave the From and To fields empty 4. Observe the result | End-to-End | From: ` ` To: ` ` | No travel cost is displayed | Chrome 149.0.7827.55 (64-bit) | The system does not display any travel cost | ❌ Fail | |

---

## 📊 Results Summary

| Metric | Value |
|--------|-------|
| Total Test Cases | 4 |
| Passed | 0 |
| Failed | 4 |
| Pass Rate | 0% |

---

## 🐛 Bug Notes

> **S3-1** — All test cases that require the Aero Taxi JSON override (t-1, t-2) result in a blank page and the following console error:
>
> `TypeError: Cannot read properties of undefined (reading 'price')`
>
> The override JSON does not include a `price` field, causing the app to crash when attempting to calculate travel cost.
>
> Additionally, the server returns `"name": "Air taxi"` — not `"Aero Taxi"` as specified in FR-AT5. This may be an additional bug worth investigating.

---

*Urban Routes QA Project 3 — TripleTen QA Engineering Program* 🎓
