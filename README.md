# Urban Scooter QA — TripleTen Final Project (QA Portfolio)

[![QA Portfolio](https://img.shields.io/badge/Focus-QA%20Engineering-blue)](https://github.com/tstewart5487-png/Final-Project-TripleTen-QA)
[![Status](https://img.shields.io/badge/Status-Portfolio-orange)]()
[![Approach-AI%20Friendly%20%2B%20Manual](https://img.shields.io/badge/Approach-AI%20Friendly%20%2B%20Manual-lightgrey)]()

Hi — I'm a QA Engineer who designs clear, high-impact test coverage and reproducible reports. This repo contains three polished QA deliverables from the TripleTen final project: web form validation, backend API tests, and mobile notification/connectivity tests.

Why recruiters should read this
- Real-world scenarios: functional test coverage exercised across UI, API, and mobile behaviors.
- Actionable outcomes: bugs triaged, reproducible steps, and suggested fixes with attached evidence.
- Tools & approach: manual exploratory testing, Postman API testing, emulator manipulation for time-sensitive flows, and defect logging (Jira).

What’s included
- UrbanScooterwebapp.md — 55 test cases for the “Who the scooter is for” form. Results: 45 passed, 10 failed; 10 bugs logged.
- UrbanRoutesAPItesting.md — 9 API test cases for courier create/delete endpoints. Results: 8 passed, 1 failed; 1 bug logged.
- APItesting.md — 24 mobile test cases (order expiry notification + offline pop-up). Results: 13 passed, 6 failed, 5 blocked; 6 bugs logged.
- main.py — PyCharm sample script (not used in QA reports; safe to remove).

Key highlights (quick recruiter TL;DR)
- Scope: UI + API + Mobile QA coverage — full-stack testing perspective.
- Notable bugs: several usability and validation defects (phone format, whitespace acceptance, offline pop-up behavior, notification scheduling).
- Reproducibility: test steps include emulator/clock manipulation and exact API payloads (Postman).

Selected metrics
- Web form: 55 cases, 45 pass, 10 fail, 10 JIRA bugs.
- API: 9 cases, 8 pass, 1 fail.
- Mobile: 24 cases, 13 pass, 6 fail, 5 blocked, 6 JIRA bugs.

How I worked
- Design: equivalence partitioning + boundary value analysis for form fields.
- API testing: Postman collections with explicit JSON request bodies and status code checks.
- Mobile: Android emulator clock/time manipulation and offline scenario testing to reproduce timing/connectivity defects.
- Reporting: test matrices, bug links to Jira, and triage notes.

Want to see more?
- Open any of the .md files to see full test steps, expected vs actual results, and Jira links to defects.
- Ask me to convert these into a portfolio site (docs/), create a one-page executive summary, or add screenshots & recordings.

Contact
- GitHub: https://github.com/tstewart5487-png
- Email: (add your preferred contact)

---
If you want, I can:
- Commit this README to the repo,
- Add LICENSE and CONTRIBUTING.md,
- Convert the reports to a simple GitHub Pages site (MkDocs) so recruiters can click through a polished docs site.
