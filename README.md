# Urban Scooter QA — TripleTen Final Project (QA Portfolio)

[![QA Portfolio](https://img.shields.io/badge/Focus-QA%20Engineering-blue)](https://github.com/tstewart5487-png/Final-Project-TripleTen-QA)
[![Status](https://img.shields.io/badge/Status-Portfolio-orange)]()
[![Approach-AI%20Friendly%20%2B%20Manual](https://img.shields.io/badge/Approach-AI%20Friendly%20%2B%20Manual-lightgrey)]()

Hi — I'm a QA Engineer who designs clear, high-impact test coverage and reproducible reports. This repository contains three polished QA deliverables created as part of the TripleTen final project. Each deliverable includes test cases, results, and links to logged defects so recruiters or hiring managers can quickly assess real-world QA skills.

## Why recruiters should read this

- Real-world scenarios: functional test coverage exercised across UI, API, and mobile behaviors.
- Actionable outcomes: bugs triaged, reproducible steps, and suggested fixes with attached evidence.
- Tools & approach: manual exploratory testing, Postman API testing, emulator manipulation for time-sensitive flows, and defect logging (Jira).

## What's included

- UrbanScooterwebapp.md — 55 test cases for the “Who the scooter is for” web form. Results: 45 passed, 10 failed; 10 bugs logged.
- UrbanRoutesAPItesting.md — 9 API test cases for courier create/delete endpoints. Results: 8 passed, 1 failed; 1 bug logged.
- APItesting.md — 24 mobile test cases (order expiry notification + offline pop-up). Results: 13 passed, 6 failed, 5 blocked; 6 bugs logged.
- main.py — PyCharm sample script (not used in QA reports; safe to remove or ignore).

Each .md file contains: test steps (preconditions, exact inputs), expected vs actual results, evidence notes, and links to the Jira tickets created during triage.

## Key highlights (quick recruiter TL;DR)

- Scope: UI + API + Mobile QA coverage — full-stack testing perspective.
- Notable bugs: usability and validation defects (phone format, whitespace acceptance), offline pop-up behavior, and notification scheduling issues.
- Reproducibility: test steps include emulator/clock manipulation and exact API payloads (Postman collections detailed in the API documents).

## Selected metrics

- Web form: 55 cases — 45 passed, 10 failed, 10 JIRA bugs.
- API: 9 cases — 8 passed, 1 failed.
- Mobile: 24 cases — 13 passed, 6 failed, 5 blocked, 6 JIRA bugs.

## How I worked

- Design: applied equivalence partitioning and boundary value analysis for form fields and inputs.
- API testing: Postman collections used with explicit JSON request bodies and status code assertions.
- Mobile testing: Android emulator clock/time manipulation and offline scenario testing to reproduce timing/connectivity defects.
- Reporting: deliverables include test matrices, bug links to Jira, screenshots, and triage notes.

## How to review the reports

1. Open the individual markdown files in this repository: UrbanScooterwebapp.md, UrbanRoutesAPItesting.md, APItesting.md.
2. Each file contains:
   - Test ID, title, preconditions
   - Step-by-step actions (including exact payloads where applicable)
   - Expected vs actual results and pass/fail status
   - Evidence and links to Jira tickets
3. Run API payloads in Postman (examples included in the API files) to reproduce API defects.
4. For mobile flows, use an Android emulator and adjust the clock or connectivity state as described in the mobile report to reproduce time-sensitive behaviors.

## Next steps I can take (if you'd like me to do them here)

- Add a LICENSE and CONTRIBUTING.md to make this repo clearer for collaborators.
- Convert the reports into a simple GitHub Pages site (MkDocs) for a polished, clickable portfolio.
- Add screenshots, short video recordings, or Postman collection export to the repo.

## Contact

- GitHub: https://github.com/tstewart5487-png
- Email: (add your preferred contact)

---

If you'd like, I will commit this updated README to the repository, add LICENSE/CONTRIBUTING, or create a docs site. Tell me which of those you'd prefer and I'll proceed.