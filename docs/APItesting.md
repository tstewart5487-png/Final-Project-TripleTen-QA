# Urban Scooter Mobile App — Notification & Connectivity Test Cases

## Overview

This is Task 2 of the TripleTen QA Engineering final project: functional testing of two features highlighted for QA coverage in the Urban Scooter mobile (courier) app — the **order expiry notification** and the **offline popup** behavior.

Test cases cover the timing and content of the 2-hour expiry notification (including layout parity with the Figma designs), and the app's behavior across every interactive element while offline, to validate offline resilience and user messaging.

**Approach:** The Android Studio emulator's clock was manipulated to test the notification threshold precisely (minute-by-minute around the 2-hour mark) without waiting in real time. Connectivity tests used the emulator's network controls to simulate offline behavior.

- **Application:** Urban Scooter Mobile App (Courier)
- **Environment:** Android Studio Emulator (API 31)
- **Feature areas tested:** 2-hour expiry notification, offline/"No Internet Connection" pop-up

## Summary

| Metric | Count |
|---|---|
| Total test cases | 24 |
| Passed | 13 |
| Failed | 6 |
| Blocked | 5 |
| Bugs filed in Jira | 6 unique bugs |

## Bugs Found

| Bug ID | Feature | Summary |
|---|---|---|
| [FPQT-11](https://tstewart5487qa.atlassian.net/browse/FPQT-11) | Notification | Notification does not appear at the 2-hour-before-expiry threshold (9:59PM) |
| [FPQT-12](https://tstewart5487qa.atlassian.net/browse/FPQT-12) | Notification | Notification does not appear while inside the app (blocked by FPQT-11) |
| [FPQT-13](https://tstewart5487qa.atlassian.net/browse/FPQT-13) | Notification | Notification does not appear on the home screen (blocked by FPQT-11) |
| [FPQT-14](https://tstewart5487qa.atlassian.net/browse/FPQT-14) | Notification | Notification does not appear with phone locked (blocked by FPQT-11) |
| [FPQT-15](https://tstewart5487qa.atlassian.net/browse/FPQT-15) | Notification | Notification content, dynamic address, expiry time, and tap-to-navigate cannot be verified — root cause is the notification not firing |
| [FPQT-25](https://tstewart5487qa.atlassian.net/browse/FPQT-25) | Connectivity | "No Internet Connection" pop-up does not appear when tapping "I don't remember the password" on the login page |
| [FPQT-26](https://tstewart5487qa.atlassian.net/browse/FPQT-26) | Connectivity | "No Internet Connection" pop-up does not appear when tapping the "Login" button |
| [FPQT-27](https://tstewart5487qa.atlassian.net/browse/FPQT-27) | Connectivity | "No Internet Connection" pop-up does not appear when tapping the logout button |
| [FPQT-28](https://tstewart5487qa.atlassian.net/browse/FPQT-28) | Connectivity | Pop-up incorrectly disappears when tapping the background app area instead of only the "OK" button |

---

## Order Expiry Notification

**Preconditions (shared):** Server is started, courier is created, order is created, courier is logged in.

| ID | Test Case | Test Steps | Expected Result | Actual Result | Status | Bug |
|---|---|---|---|---|---|---|
| 1 | Verify notification doesn't arrive more than 2 hours before expiry (9:58PM) | Accept order → set date to order date → set time to 9:57PM → wait until 9:58PM | Notification doesn't appear | … |
| 2 | Verify notification arrives at exactly 2 hours before expiry (9:59PM) | Accept order → set date to order date → set time to 9:57PM → wait until 9:59PM | Notification appears | Notification doesn't appear | Fail | [FPQT-11]
| 3 | Verify notification doesn't arrive every minute below the 2-hour threshold (10:00PM) | Accept order → set date to order date → set time to 9:57PM → wait until 10:00PM | Notification doesn't appear | … |
| 4 | Verify notification appears while inside the app | Accept order → set date to order date → set time to 9:57PM → wait until 9:59PM | Notification appears | Notification doesn't appear | Fail | [FPQT-12]
| 5 | Verify notification appears on the home screen | Same as above | Notification appears | Notification doesn't appear | Blocked | [FPQT-13]
| 6 | Verify notification appears with phone locked | Same as above | Notification appears | Notification doesn't appear | Blocked | [FPQT-14]

## "No Internet Connection" Pop-Up

**Preconditions (shared):** Server is started, courier is created, order is created; Wi-Fi and cell service disabled on the Android emulator.

| ID | Test Case | Test Steps | Expected Result | Actual Result | Status | Bug |
|---|---|---|---|---|---|---|
| 11 | Verify pop-up appears when clicking "I don't remember the password" on login page | Navigate to login page → click link | Pop-up appears | Pop-up does not appear | Fail | [FPQT-25]
| 12 | Verify pop-up appears when clicking "Login" button | Enter credentials → click Login | Pop-up appears | Pop-up does not appear | Fail | [FPQT-26]
| 13 | Verify pop-up appears when clicking "All orders" title card (orders page) | Courier logged in → click "All orders" | Pop-up appears | Pop-up appears | Pass | |
| 14 | Verify pop-up appears when clicking "My orders" title card (orders page) | Courier logged in → click "My orders" | Pop-up appears | Pop-up appears | Pass | |
