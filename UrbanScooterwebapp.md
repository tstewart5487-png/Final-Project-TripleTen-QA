# Urban Scooter Web App — "About Customer" Form Test Cases

## Overview

This is Task 1 of the TripleTen QA Engineering final project: functional and validation testing of the **"Who the scooter is for"** form — the first stage of the "Place Order" flow in the Urban Scooter web application.

The goal was to design a sufficient set of positive and negative test cases to validate each field on the form (First Name, Last Name, Address, Subway Station, Phone), execute those tests cross-browser, and file any defects found in Jira.

**Approach:** Test cases were designed using equivalence partitioning and boundary value analysis for each field — testing valid ranges, just-inside/just-outside boundaries, allowed and disallowed character sets, required-field behavior, and error-state messaging/recovery.

- **Application:** Urban Scooter Web App
- **Browsers tested:** Google Chrome (85+), Opera (71+)
- **Resolution:** 1280x720
- **Fields under test:** First Name, Last Name, Address, Subway Station, Phone

## Summary

| Metric | Count |
|---|---|
| Total test cases | 55 |
| Passed (both browsers) | 45 |
| Failed (both browsers) | 10 |
| Bugs filed in Jira | 10 |

## Bugs Found

| Bug ID | Field | Summary |
|---|---|---|
| [FPQT-1](https://tstewart5487qa.atlassian.net/jira/software/projects/FPQT/boards/135?selectedIssue=FPQT-1) | First Name | Whitespace-only input is accepted (should be rejected) |
| [FPQT-2](https://tstewart5487qa.atlassian.net/jira/software/projects/FPQT/boards/135?selectedIssue=FPQT-2) | First Name | Error message does not match expected text "Enter correct name." |
| [FPQT-3](https://tstewart5487qa.atlassian.net/jira/software/projects/FPQT/boards/135?selectedIssue=FPQT-3) | Last Name | Field accepts more than 15 characters |
| [FPQT-4](https://tstewart5487qa.atlassian.net/jira/software/projects/FPQT/boards/135?selectedIssue=FPQT-4) | Last Name | Whitespace-only input is accepted (should be rejected) |
| [FPQT-5](https://tstewart5487qa.atlassian.net/browse/FPQT-5) | Last Name | Error message does not match expected text "Enter a valid last name." |
| [FPQT-6](https://tstewart5487qa.atlassian.net/browse/FPQT-6) | Address | Empty Address field is accepted (should be required) |
| [FPQT-7](https://tstewart5487qa.atlassian.net/browse/FPQT-7) | Address | Error message does not match expected text "Enter a valid address" |
| [FPQT-8](https://tstewart5487qa.atlassian.net/browse/FPQT-8) | Phone | Ambiguity/defect in accepted length range (10–12 chars incl. "+") |
| [FPQT-9](https://tstewart5487qa.atlassian.net/browse/FPQT-9) | Phone | Field accepts more than 12 characters |
| [FPQT-10](https://tstewart5487qa.atlassian.net/browse/FPQT-10) | Phone | Error message does not match expected text "Enter a valid phone number." |
| [FPQT-32](https://tstewart5487qa.atlassian.net/browse/FPQT-32) | Phone | Missing "+" symbol is accepted (should be required) |

---

## First Name Field

| ID | Test Case | Test Data | Expected Result | Chrome | Opera | Bug |
|---|---|---|---|---|---|---|
| 1 | Verify 2–15 characters are allowed | Theodore (8) | 2–15 characters accepted | Pass | Pass | |
| 2 | Verify invalid length <2 is rejected | T (1) | <2 characters rejected | Pass | Pass | |
| 3 | Verify invalid length >15 is rejected | Theodoreandrewiii (17) | >15 characters rejected | Pass | Pass | |
| 4 | Verify field accepts Latin letters | Theodore | Latin letters accepted | Pass | Pass | |
| 5 | Verify field accepts spaces | Theodore A | Spaces accepted | Pass | Pass | |
| 6 | Verify field accepts dashes | Theodore-A | Dashes accepted | Pass | Pass | |
| 7 | Verify numbers are rejected | Theo123 | Numbers rejected | Pass | Pass | |
| 8 | Verify special characters are rejected | Theo@# | Special characters rejected | Pass | Pass | |
| 9 | Verify non-Latin characters are rejected | Алекс | Non-Latin characters rejected | Pass | Pass | |
| 10 | Verify field is required | (empty) | Cannot proceed with empty field | Pass | Pass | |
| 11 | Verify whitespace-only input is rejected | "   " (3 spaces) | Whitespace-only rejected | **Fail** | **Fail** | [FPQT-1](https://tstewart5487qa.atlassian.net/jira/software/projects/FPQT/boards/135?selectedIssue=FPQT-1) |
| 12 | Verify error message text | Алекс | Message: "Enter correct name." | **Fail** | **Fail** | [FPQT-2](https://tstewart5487qa.atlassian.net/jira/software/projects/FPQT/boards/135?selectedIssue=FPQT-2) |
| 13 | Verify error state clears on correction | Алекс → Theodore | Error clears, valid input accepted | Pass | Pass | |

## Last Name Field

| ID | Test Case | Test Data | Expected Result | Chrome | Opera | Bug |
|---|---|---|---|---|---|---|
| 14 | Verify 2–15 characters are allowed | Theodore (8) | 2–15 characters accepted | Pass | Pass | |
| 15 | Verify invalid length <2 is rejected | T (1) | <2 characters rejected | Pass | Pass | |
| 16 | Verify invalid length >15 is rejected | Theodoreandrewiii (17) | >15 characters rejected | **Fail** | **Fail** | [FPQT-3](https://tstewart5487qa.atlassian.net/jira/software/projects/FPQT/boards/135?selectedIssue=FPQT-3) |
| 17 | Verify field accepts Latin letters | Theodore | Latin letters accepted | Pass | Pass | |
| 18 | Verify field accepts spaces | Theodore A | Spaces accepted | Pass | Pass | |
| 19 | Verify field accepts dashes | Theodore-A | Dashes accepted | Pass | Pass | |
| 20 | Verify numbers are rejected | Theo123 | Numbers rejected | Pass | Pass | |
| 21 | Verify special characters are rejected | Theo@# | Special characters rejected | Pass | Pass | |
| 22 | Verify non-Latin characters are rejected | Алекс | Non-Latin characters rejected | Pass | Pass | |
| 23 | Verify field is required | (empty) | Cannot proceed with empty field | Pass | Pass | |
| 24 | Verify whitespace-only input is rejected | "   " (3 spaces) | Whitespace-only rejected | **Fail** | **Fail** | [FPQT-4](https://tstewart5487qa.atlassian.net/jira/software/projects/FPQT/boards/135?selectedIssue=FPQT-4) |
| 25 | Verify error message text | Алекс | Message: "Enter a valid last name." | **Fail** | **Fail** | [FPQT-5](https://tstewart5487qa.atlassian.net/browse/FPQT-5) |
| 26 | Verify error state clears on correction | Theo123 → Theodore A | Error clears, valid input accepted | Pass | Pass | |

## Address Field

| ID | Test Case | Test Data | Expected Result | Chrome | Opera | Bug |
|---|---|---|---|---|---|---|
| 27 | Verify field is required | (empty) | Empty field rejected | **Fail** | **Fail** | [FPQT-6](https://tstewart5487qa.atlassian.net/browse/FPQT-6) |
| 28 | Verify 5–50 characters are accepted | 123 Main Street | 5–50 characters accepted | Pass | Pass | |
| 29 | Verify <5 characters are rejected | 123A (4) | <5 characters rejected | Pass | Pass | |
| 30 | Verify >50 characters are rejected | 53-char string | >50 characters rejected | Pass | Pass | |
| 31 | Verify field accepts Latin letters | MainStAp | Latin letters accepted | Pass | Pass | |
| 32 | Verify field accepts numbers | Main St Ap 4 | Numbers accepted | Pass | Pass | |
| 33 | Verify field accepts spaces | Main St Ap | Spaces accepted | Pass | Pass | |
| 34 | Verify field accepts dashes | Main St Apt - B | Dashes accepted | Pass | Pass | |
| 35 | Verify field accepts dots | Main St. Apt | Dots accepted | Pass | Pass | |
| 36 | Verify field accepts commas | Main St, Apt | Commas accepted | Pass | Pass | |
| 37 | Verify special characters are rejected | 123 Main St. $5 | Special characters rejected | Pass | Pass | |
| 38 | Verify non-Latin characters are rejected | ул. Ленина, 12 | Non-Latin characters rejected | Pass | Pass | |
| 39 | Verify leading/trailing spaces are trimmed | " 123 Main St. " | Spaces trimmed on blur | Pass | Pass | |
| 40 | Verify trimmed length <5 triggers error | " 123A " | Trimmed to "123A", error shown | Pass | Pass | |
| 41 | Verify error message text | ул. Ленина, 12 | Message: "Enter a valid address" | — | — | [FPQT-7](https://tstewart5487qa.atlassian.net/browse/FPQT-7) |
| 42 | Verify error state clears on correction | ул. Ленина, 12 → Main St, Apt | Error clears, valid input accepted | Pass | Pass | |

## Subway Station Field

| ID | Test Case | Test Data | Expected Result | Chrome | Opera | Bug |
|---|---|---|---|---|---|---|
| 43 | Verify field is required | (empty) | Cannot order without a station selected | Pass | Pass | |
| 44 | Verify partial name shows matching suggestions | "Uni" | Dropdown shows matching stations | Pass | Pass | |
| 45 | Verify clicking a suggestion selects it | "Union" → click "Union Station" | Dropdown closes, station populated | Pass | Pass | |
| 46 | Verify invalid input shows no dropdown | xyzmk | Dropdown does not appear | Pass | Pass | |

## Phone Field

| ID | Test Case | Test Data | Expected Result | Chrome | Opera | Bug |
|---|---|---|---|---|---|---|
| 47 | Verify 10–12 characters (incl. "+") are accepted | +0123456789 (11) | 10–12 characters incl. "+" accepted | **Fail** | **Fail** | [FPQT-8](https://tstewart5487qa.atlassian.net/browse/FPQT-8) |
| 48 | Verify field cannot be empty | (empty) | Empty input rejected | Pass | Pass | |
| 49 | Verify invalid length <10 is rejected | +01234567 (9) | <10 characters rejected | Pass | Pass | |
| 50 | Verify invalid length >12 is rejected | +012345678901 (13) | >12 characters rejected | **Fail** | **Fail** | [FPQT-9](https://tstewart5487qa.atlassian.net/browse/FPQT-9) |
| 51 | Verify "+" symbol is required | 12345678901 | Missing "+" rejected | **Fail** | **Fail** | [FPQT-32](https://tstewart5487qa.atlassian.net/browse/FPQT-32) |
| 52 | Verify "+" is rejected if misplaced | 123+4567890 | Misplaced "+" rejected | Pass | Pass | |
| 53 | Verify letters are rejected | +phone number | Letters rejected | Pass | Pass | |
| 54 | Verify special characters (excl. "+") are rejected | +!@#$%^&*()_ | Special characters rejected | Pass | Pass | |
| 56 | Verify non-Latin characters are rejected | +1234567890ГД | Non-Latin characters rejected | Pass | Pass | |
| 57 | Verify multiple "+" symbols are rejected | ++12345678 | Multiple "+" rejected | Pass | Pass | |
| 58 | Verify spaces inside the number are rejected | +123 456 7890 | Spaces rejected | Pass | Pass | |
| 59 | Verify error message text | +1234567890ГД | Message: "Enter a valid phone number." | **Fail** | **Fail** | [FPQT-10](https://tstewart5487qa.atlassian.net/browse/FPQT-10) |
| 60 | Verify error state clears on correction | +1234567890ГД → +0123456789 | Error clears, valid input accepted | Pass | Pass | |

---

### Notes

- **FPQT-8 / FPQT-9:** The requirements are ambiguous about whether the "+" symbol counts toward the 10–12 character range or sits outside it. The requirements state *"Only numbers and '+' symbol. Length should be 10–12 characters. A plus sign is required,"* without clarifying whether that means "+ plus 10-12 digits" or "+ included in the 10-12 count." Based on this ambiguity, the 10-character value (`+012345678`) was not accepted and the 13-character value (`+012345678901`) was — flagged for clarification/defect.