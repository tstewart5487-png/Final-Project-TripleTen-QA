# Urban Scooter Web App — "About Customer" Form Test Cases

## Overview

This is Task 1 of the TripleTen QA Engineering final project: functional and validation testing of the **"Who the scooter is for"** form — the first stage of the "Place Order" flow in the Urban Scooter web app.

The goal was to design a sufficient set of positive and negative test cases to validate each field on the form (First Name, Last Name, Address, Subway Station, Phone), execute those tests cross-browser, and record reproducible evidence and Jira tickets for defects found.

**Approach:** Test cases were designed using equivalence partitioning and boundary value analysis for each field — testing valid ranges, just-inside/just-outside boundaries, allowed and disallowed characters, and error messaging.

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
| 11 | Verify whitespace-only input is rejected | "   " (3 spaces) | Whitespace-only rejected | **Fail** | **Fail** | [FPQT-1](https://tstewart5487qa.atlassian.net/jira/software/projects/FPQT/boar[...]
| 12 | Verify error message text | Алекс | Message: "Enter correct name." | **Fail** | **Fail** | [FPQT-2](https://tstewart5487qa.atlassian.net/jira/software/projects/FPQT/boards/135?selected[...]
| 13 | Verify error state clears on correction | Алекс → Theodore | Error clears, valid input accepted | Pass | Pass | |

## Last Name Field

| ID | Test Case | Test Data | Expected Result | Chrome | Opera | Bug |
|---|---|---|---|---|---|---|
| 14 | Verify 2–15 characters are allowed | Theodore (8) | 2–15 characters accepted | Pass | Pass | |
| 15 | Verify invalid length <2 is rejected | T (1) | <2 characters rejected | Pass | Pass | |
| 16 | Verify invalid length >15 is rejected | Theodoreandrewiii (17) | >15 characters rejected | **Fail** | **Fail** | [FPQT-3](https://tstewart5487qa.atlassian.net/jira/software/projects/FPQT/bo[...]
| 17 | Verify field accepts Latin letters | Theodore | Latin letters accepted | Pass | Pass | |
| 18 | Verify field accepts spaces | Theodore A | Spaces accepted | Pass | Pass | |
| 19 | Verify field accepts dashes | Theodore-A | Dashes accepted | Pass | Pass | |
| 20 | Verify numbers are rejected | Theo123 | Numbers rejected | Pass | Pass | |
| 21 | Verify special characters are rejected | Theo@# | Special characters rejected | Pass | Pass | |
| 22 | Verify non-Latin characters are rejected | Алекс | Non-Latin characters rejected | Pass | Pass | |
| 23 | Verify field is required | (empty) | Cannot proceed with empty field | Pass | Pass | |
| 24 | Verify whitespace-only input is rejected | "   " (3 spaces) | Whitespace-only rejected | **Fail** | **Fail** | [FPQT-4](https://tstewart5487qa.atlassian.net/jira/software/projects/FPQT/boar[...]
| 25 | Verify error message text | Алекс | Message: "Enter a valid last name." | **Fail** | **Fail** | [FPQT-5](https://tstewart5487qa.atlassian.net/browse/FPQT-5) |
| 26 | Verify error state clears on correction | Theo123 → Theodore A | Error clears, valid input accepted | Pass | Pass | |
