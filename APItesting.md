# Urban Scooter Mobile App — Notification & Connectivity Test Cases

## Overview

This is Task 2 of the TripleTen QA Engineering final project: functional testing of two features highlighted for QA coverage in the Urban Scooter mobile (courier) app — the **order expiry notification** and the app's **offline / "No Internet Connection" handling**.

Test cases cover the timing and content of the 2-hour expiry notification (including layout parity with the Figma designs), and the app's behavior across every interactive element while offline, to confirm the "No Internet Connection" pop-up appears consistently for any action requiring network access and is dismissed only through the intended interaction.

**Approach:** The Android Studio emulator's clock was manipulated to test the notification threshold precisely (minute-by-minute around the 2-hour mark) without waiting in real time. Connectivity tests were run with Wi-Fi and cellular disabled on the emulator, exercising each button/link across the login, orders, and My Orders screens.

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
| [FPQT-15](https://tstewart5487qa.atlassian.net/browse/FPQT-15) | Notification | Notification content, dynamic address, expiry time, and tap-to-navigate cannot be verified — root cause is the notification not appearing (blocked by FPQT-11) |
| [FPQT-25](https://tstewart5487qa.atlassian.net/browse/FPQT-25) | Connectivity | "No Internet Connection" pop-up does not appear when tapping "I don't remember the password" on the login page |
| [FPQT-26](https://tstewart5487qa.atlassian.net/browse/FPQT-26) | Connectivity | "No Internet Connection" pop-up does not appear when tapping the "Login" button |
| [FPQT-27](https://tstewart5487qa.atlassian.net/browse/FPQT-27) | Connectivity | "No Internet Connection" pop-up does not appear when tapping the logout button |
| [FPQT-28](https://tstewart5487qa.atlassian.net/browse/FPQT-28) | Connectivity | Pop-up incorrectly disappears when tapping the background app area instead of only the "OK" button |

---

## Order Expiry Notification

**Preconditions (shared):** Server is started, courier is created, order is created, courier is logged in.

| ID | Test Case | Test Steps | Expected Result | Actual Result | Status | Bug |
|---|---|---|---|---|---|---|
| 1 | Verify notification doesn't arrive more than 2 hours before expiry (9:58PM) | Accept order → set date to order date → set time to 9:57PM → wait until 9:58PM | Notification doesn't appear | Notification doesn't appear | Pass | |
| 2 | Verify notification arrives at exactly 2 hours before expiry (9:59PM) | Accept order → set date to order date → set time to 9:57PM → wait until 9:59PM | Notification appears | Notification doesn't appear | **Fail** | [FPQT-11](https://tstewart5487qa.atlassian.net/browse/FPQT-11) |
| 3 | Verify notification doesn't arrive every minute below the 2-hour threshold (10:00PM) | Accept order → set date to order date → set time to 9:57PM → wait until 10:00PM | Notification doesn't appear | Notification doesn't appear | Pass | |
| 4 | Verify notification appears while inside the app | Accept order → set date to order date → set time to 9:57PM → wait until 9:59PM | Notification appears | Notification doesn't appear | Blocked | [FPQT-12](https://tstewart5487qa.atlassian.net/browse/FPQT-12) |
| 5 | Verify notification appears on the home screen | Same as above | Notification appears | Notification doesn't appear | Blocked | [FPQT-13](https://tstewart5487qa.atlassian.net/browse/FPQT-13) |
| 6 | Verify notification appears with phone locked | Same as above | Notification appears | Notification doesn't appear | Blocked | [FPQT-14](https://tstewart5487qa.atlassian.net/browse/FPQT-14) |
| 7 | Verify notification text/formatting matches Figma | Order created with address "State St 1214" → same steps as above | Notification reads: 2 hours to end of order, address, 11:59PM deadline, support contact 0101 | Notification doesn't appear | Blocked | [FPQT-15](https://tstewart5487qa.atlassian.net/browse/FPQT-15) |
| 8 | Verify notification dynamically populates custom address | Order created with address "Main St 500" → same steps as above | Notification text reflects "Main St 500" | Notification doesn't appear | Blocked | [FPQT-15](https://tstewart5487qa.atlassian.net/browse/FPQT-15) |
| 9 | Verify notification displays fixed default expiry time (11:59PM) | Same as above | Time field reads "11:59PM" | Notification doesn't appear | Blocked | [FPQT-15](https://tstewart5487qa.atlassian.net/browse/FPQT-15) |
| 10 | Verify tapping the notification navigates to "My Orders" | Order created with address "State St 1214" → same steps as above → tap notification | Navigates to "My Orders" tab | Notification doesn't appear | Blocked | [FPQT-15](https://tstewart5487qa.atlassian.net/browse/FPQT-15) |

**Notes:** Test cases 4–10 are all blocked by the root-cause defect in test case 2 (FPQT-11) — the notification does not fire at the expected threshold, so downstream behavior (content, dynamic data, navigation) cannot be verified until that's fixed.

## "No Internet Connection" Pop-Up

**Preconditions (shared):** Server is started, courier is created, order is created; Wi-Fi and cell service disabled on the Android emulator.

| ID | Test Case | Test Steps | Expected Result | Actual Result | Status | Bug |
|---|---|---|---|---|---|---|
| 11 | Verify pop-up appears when clicking "I don't remember the password" on login page | Navigate to login page → click link | Pop-up appears | Pop-up does not appear | **Fail** | [FPQT-25](https://tstewart5487qa.atlassian.net/browse/FPQT-25) |
| 12 | Verify pop-up appears when clicking "Login" button | Enter credentials → click Login | Pop-up appears | Pop-up does not appear | **Fail** | [FPQT-26](https://tstewart5487qa.atlassian.net/browse/FPQT-26) |
| 13 | Verify pop-up appears when clicking "All orders" title card (orders page) | Courier logged in → click "All orders" | Pop-up appears | Pop-up appears | Pass | |
| 14 | Verify pop-up appears when clicking "My orders" title card (orders page) | Courier logged in → click "My orders" | Pop-up appears | Pop-up appears | Pass | |
| 15 | Verify pop-up appears when clicking logout button (orders page) | Courier logged in → click logout | Pop-up appears | Pop-up does not appear | **Fail** | [FPQT-27](https://tstewart5487qa.atlassian.net/browse/FPQT-27) |
| 16 | Verify pop-up appears when clicking "Accept" (orders page) | Courier logged in → click Accept | Pop-up appears | Pop-up appears | Pass | |
| 17 | Verify pop-up appears when clicking "My orders" title card (My Orders page) | Navigate to My Orders page → click "My orders" | Pop-up appears | Pop-up appears | Pass | |
| 18 | Verify pop-up appears when clicking "All orders" title card (My Orders page) | Navigate to My Orders page → click "All orders" | Pop-up appears | Pop-up appears | Pass | |
| 19 | Verify pop-up appears when clicking active order (My Orders page) | Accept order → navigate to My Orders → click "Complete" | Pop-up appears | Pop-up appears | Pass | |
| 20 | Verify pop-up disappears when tapping "OK" | Pop-up is visible → tap "OK" | Pop-up disappears | Pop-up disappears | Pass | |
| 21 | Verify pop-up reappears after "OK" when retrying an active button offline | Click "All orders" → tap "OK" → tap whitespace → click "All orders" again | Pop-up reappears | Pop-up reappears | Pass | |
| 22 | Verify pop-up does not dismiss when tapping inside the pop-up whitespace | Tap whitespace inside pop-up box | Pop-up remains open | Pop-up remains open | Pass | |
| 23 | Verify pop-up does not dismiss when tapping the background app | Click "All orders" → tap whitespace outside the pop-up | Pop-up remains open | Pop-up disappears | **Fail** | [FPQT-28](https://tstewart5487qa.atlassian.net/browse/FPQT-28) |
| 24 | Verify pop-up text and layout match Figma | Click "Accept" on an available order | Pop-up matches Figma design | Pop-up matches Figma design | Pass | |

### Notes

- **FPQT-25 / FPQT-27:** The requirements are ambiguous about what qualifies as an "active button" in relation to the offline pop-up. It's unclear whether this means a literal button element or any clickable text/link that navigates. These test cases assume the broader interpretation (any clickable navigation element). For the logout case specifically (FPQT-27), it's plausible the app is intentionally handling logout locally/offline by design — logging out doesn't require a network call — but since the button could still be read as "active" per the requirements, it's flagged as a defect for clarification rather than assumed to be correct behavior.