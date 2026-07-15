---
type: resource
status: active
created: 2026-07-15
author: ai
---

# NetSuite App Dev Hub

Prep hub for the **NetSuite Certified Application Developer** exam — Gabriel has purchased the exam and needs to sit for it. This is the immediate priority; Claude certs come after (see [[Claude Certification Hub]] — Associate first, then build toward Architect).

## Exam Facts (official, March 2024 study guide)
| Item | Detail |
|---|---|
| Fee | **$250** ($150 retake) |
| Format | **60 multiple-choice, 90 minutes** |
| Delivery | **Live proctored — no reference materials allowed** |
| Passing score | Not published |
| Part of | NetSuite Certified SuiteCloud Developer (also needs Web Services Developer + SuiteFoundation) |
| Candidate | 1–2 yrs SuiteCloud, 2–3 yrs dev; JavaScript, SQL, JSON, HTML, XML |

## The 5 Subject Areas → one note each
1. [[NAD - SuiteScript 2.1]] — the biggest area (9 objectives): script types, entry points, records, UI, Map/Reduce, i18n
2. [[NAD - SuiteFlow]] — workflow states, actions, transitions, triggers, client vs server
3. [[NAD - SuiteBuilder]] — Advanced PDF/HTML templates (FreeMarker/BFO), custom fields/records/segments
4. [[NAD - SDF]] — Account Customization vs SuiteApp, manifest/deploy, SuiteCloud CLI
5. [[NAD - Performance and Security]] — User Event perf, governance, N/cache, roles & credentials

Each note has: a **story** to anchor the concepts, a **key-facts** block, and **6 practice questions** with answers + explanations. Official sample questions are marked ⭐.

**Full mock drill:** [[NAD - Question Bank 60]] — 60 more questions (no repeats), weighted like the real exam, answer key at the bottom. Total practice pool ≈ **90 questions**.

**📱 Interactive quiz (phone-friendly):** https://nazir99.github.io/netsuite-app-dev-quiz/ — all 90 questions, tap-to-answer, instant scoring, every option explains why it's right/wrong. Hosted on GitHub Pages (repo: `nazir99/netsuite-app-dev-quiz`, public). Source `index.html` lives in that repo.

## Source materials (on this computer)
- `~/Documents/Application-Developer-Exam-Study-Guide.pdf` — the blueprint
- `~/Documents/Application-Developer-Certification-Sample-Test.pdf` — 23 official sample Qs + answer key
- Recommended NetSuite MyLearn courses: *SuiteScript 2.0: Extend NetSuite*, *SDF: Building & Deploying CD.2*, *Performance Strategies in SuiteScript*, *SuiteScript 2.1: Query API & SuiteQL*, *Custom UI Development*, *SuiteFlow Fundamentals* + *Advanced*, *Advanced PDF/HTML Templates*

## Study plan
- [ ] Read all 5 section notes; drill the 30 practice questions
- [ ] Re-take the official sample test cold — aim 100%
- [ ] Weak areas → the matching MyLearn course + Records Browser / Help Center
- [ ] Hands-on: write one script per type (Client, UE, Suitelet, Map/Reduce, RESTlet) in a sandbox
- [ ] Book the proctored slot

> You already run ICR SuiteQL and hybrid-costing SuiteScript at HGS — lean on that. The exam rewards knowing *which tool for which scenario*, not memorizing syntax.
