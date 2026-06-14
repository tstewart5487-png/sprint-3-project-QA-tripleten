# 💳 Card Payment Fields — Equivalence Partitioning & Boundary Value Analysis

> Analysis for FR-CS33 of the Urban Routes Carsharing feature.

---

## 📋 Requirement

**FR-CS33:** The following limits shall be applied to the input fields for card payments:

| Field | Limits |
|-------|--------|
| Card Number | Any input besides numbers is incorrect and the system will not allow it. No more than 12 characters are allowed. The input format is: `nnnn nnnn nnnn`. The boundary values are 0000 and 9999, inclusive. Spaces between numbers will be automatically added when the field is not in focus. The "Add" button will remain inactive if the input length is less than 12 characters. |
| CVV/CVC | Any input besides numbers is incorrect and the system will not allow it. No more than 2 characters are allowed. The input format is: `nn`. The boundary values are 01 and 99, inclusive. The "Add" button will remain inactive if the input length is less than 2 characters. |

---

## 💳 Card Number Field

| Class | BVA Values | Test Data Example | EP & BVA Values | Notes |
|-------|-----------|-------------------|-----------------|-------|
| Numbers only | | `0000 0000 0000` | | Valid input type |
| Letters only | | `abcd efgh ijkl` | | Invalid input type |
| Non-Latin characters | | `あいうえおかきくけこさし` | | Invalid input type |
| Mix of letters and numbers | | `abcd 0000 0000` | | Invalid input type |
| Special characters | | `!!!! @@@@ ####` | | Invalid input type |
| 0–12 characters (valid length) | 0,1,11,12,13 | `0000 0000 0000` (12) | `""` (0) `0` (1) `0000 0000 000` (11) `0000 0000 0000` (12) `0000 0000 00000` (13) | Within allowed range. 0,1 lower BVA. 11,12,13 upper 3-value BVA |
| 13+ characters (invalid length) | 12,13,14 | `0000 0000 00000` (13) | `0000 0000 0000` (12) `0000 0000 00000` (13) `0000 0000 000000` (14) | Outside allowed range. 12,13,14 invalid 3-value BVA |
| Correct format | | `0000 0000 0000` | | Spaces auto-added on blur |
| Incorrect format | | `000000000000` | | Missing spaces |
| Valid range (lower boundary) | 0000,0001 | `0000 0000 0000` | `0000 0000 0000` (lower BV) `0001 0000 0000` (1 above lower BV) | Lower boundary 3-value BVA |
| Valid range (upper boundary) | 9998,9999 | `9999 9999 9999` | `9998 9999 9999` (1 below upper BV) `9999 9999 9999` (upper BV) | Upper boundary 3-value BVA |
| "Add" button inactive | 10,11 | `0000 0000 000` (11) | `0000 0000 00` (10) `0000 0000 000` (11) | Button inactive below 12 chars |
| "Add" button active | 11,12,13 | `0000 0000 0000` (12) | `0000 0000 000` (11) `0000 0000 0000` (12) `0000 0000 00000` (13) | Button active at 12 chars |

---

## 🔒 CVV/CVC Field

| Class | BVA Values | Test Data Example | EP & BVA Values | Notes |
|-------|-----------|-------------------|-----------------|-------|
| Numbers only | | `11` | | Valid input type |
| Letters only | | `aa` | | Invalid input type |
| Non-Latin characters | | `あい` | | Invalid input type |
| Mix of letters and numbers | | `a1` | | Invalid input type |
| Special characters | | `!@` | | Invalid input type |
| Input is 2 characters (valid) | 1,2,3 | `11` (2) | `1` (1) `11` (2) `111` (3) | Within allowed range. 1,2,3 BVA |
| Less than 2 characters (invalid) | 0,1,2 | `1` (1) | `""` (0) `1` (1) `11` (2) | Outside allowed range. 0,1 lower BVA |
| More than 2 characters (invalid) | 2,3,4 | `111` (3) | `11` (2) `111` (3) `1111` (4) | Outside allowed range. 2,3,4 upper 3-value BVA |
| Correct format | | `11` | | Format: `nn` |
| Incorrect format | | `1 1` | | Spaces not allowed |
| Lower boundary | 00,01,02 | `01` | `00` (1 below lower BV) `01` (lower BV) `02` (1 above lower BV) | Lower boundary 3-value BVA |
| Upper boundary | 98,99 | `99` | `98` (1 below upper BV) `99` (upper BV) | Upper boundary 3-value BVA |
| "Add" button inactive | 0,1 | `1` (1) | `""` (0) `1` (1) | Button inactive below 2 chars |
| "Add" button active | 1,2,3 | `11` (2) | `1` (1) `11` (2) `111` (3) | Button active at 2 chars |

---

*Urban Routes QA Project 3 — TripleTen QA Engineering Program* 🎓
