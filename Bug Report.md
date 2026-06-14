# 🐛 Bug Report — S3-1

> Urban Routes QA Project 3 — TripleTen QA Engineering Program

---

## Summary

App throws `TypeError: Cannot read properties of undefined (reading 'price')` when Aero Taxi JSON override is applied — total travel time and cost are not displayed.

---

## Bug Details

| Field | Details |
|-------|---------|
| **Bug ID** | S3-1 |
| **Feature** | Aero Taxi |
| **Severity** | High |
| **Status** | Open |
| **Environment** | Chrome 149.0.7827.55 (Official Build) (64-bit) |
| **Application Version** | Urban Routes v2.0 |
| **Jira Link** | [S3-1](https://tstewart5487qa.atlassian.net/jira/software/projects/S3/boards/35?selectedIssue=S3-1) |

---

## Steps to Reproduce

1. Open the Urban Routes app in Chrome
2. Open **DevTools** (`F12`)
3. Navigate to the **Network** panel
4. Search for `types` in the search field
5. Right-click the `types` JSON file and select **Override content**
6. Paste the following Aero Taxi JSON over the existing content:

```json
[{"id":"car","name":"Car","icons":{"inactive":"car.svg","active":"car-active.svg"}},{"id":"walk","name":"Walk","icons":{"inactive":"walk.svg","active":"walk-active.svg"}},{"id":"taxi","name":"Taxi","icons":{"inactive":"taxi.svg","active":"taxi-active.svg"}},{"id":"bike","name":"Bike","icons":{"inactive":"bike.svg","active":"bike-active.svg"}},{"id":"scooter","name":"Scooter","icons":{"inactive":"scooter.svg","active":"scooter-active.svg"}},{"id":"drive","name":"Drive","icons":{"inactive":"car.svg","active":"car-active.svg"}},{"id":"aero","name":"Air taxi","icons":{"inactive":"helicopter.svg","active":"helicopter-active.svg"}}]
```

7. Save with `Ctrl+S` and reload the page
8. Enter `East` in the **From** field
9. Enter `1300` in the **To** field
10. Select **Custom** mode
11. Click the **Aero Taxi** icon
12. Observe the result

---

## Expected Result

The calculation result displays the total travel time and cost for the Aero Taxi service.

---

## Actual Result

The page goes blank. No travel time or cost is displayed. The following error is thrown in the console:

```
TypeError: Cannot read properties of undefined (reading 'price')
  at App.js:284:24
  at Et (App.js:352:31)
```

---

## Console Screenshot

> `TypeError: Cannot read properties of undefined (reading 'price')` visible in Chrome DevTools console panel at `App.js:284`.

---

## Root Cause Analysis

The Aero Taxi override JSON does not include a `price` field. When the app attempts to read the price from the server response, the value is `undefined`, causing the app to crash.

---

## Additional Notes

> ⚠️ A secondary issue was also identified during testing: the server returns `"name": "Air taxi"` in the JSON response, while **FR-AT5** states the result should display `"Aero Taxi"`. This may be an additional bug requiring investigation.

---

## Test Cases Affected

| Test Case ID | Description | Status |
|-------------|-------------|--------|
| t-1 | The system should display the total travel time correctly | ❌ Fail |
| t-2 | The system should display the total travel cost correctly | ❌ Fail |

---

*Urban Routes QA Project 3 — TripleTen QA Engineering Program* 🎓
