---
type: resource
status: active
created: 2026-07-15
author: ai
---

# NAD - Performance and Security

Make it fast, make it safe. Part of [[NetSuite App Dev Hub]].

## The story
A user complains that saving a Sales Order takes almost a minute. You open Scripted Records and find **eight User Event scripts** on that record — every save fires all eight, in sequence. Some are yours; some are managed. This is the performance heart of the exam: **every User Event adds to the save time**, so the fixes are to **consolidate** your own scripts into one, filter execution by **context** and **event type** so scripts only run when they must, and offload anything heavy to a **Scheduled or Map/Reduce** script via **`N/task`** rather than doing it inline. Choosing the right API matters too — `search.lookupFields` beats `record.load` for a few fields; `N/cache` avoids recomputing the same data every execution; Map/Reduce yields governance between stages so big jobs don't hit unit limits. On the security side, the rule is **least privilege**: run scripts with the **minimally required role**, configure the Script Deployment's **Audience**, **Execute as Role**, and **Available without Login** carefully (especially for Suitelets/RESTlets), never log credentials or sensitive data, and use **`N/crypto`** to encrypt/decipher values, **`N/credentials`** for stored secrets.

## Key facts
- **Every User Event script adds to a record's save time.** Reduce count: consolidate your own into one; filter by **context type** and **event type** so they run only when needed.
- Offload long-running work from a UE script to a scheduled/Map-Reduce job with **`N/task`**.
- API efficiency: `lookupFields` < `record.load`; `N/cache` for repeated data; SuiteQL/`N/query` for heavy joins; Map/Reduce **yields governance between stages**. Mind **usage units** and search/query limits.
- RESTlet throughput scales with **integration concurrency** / **SuiteCloud Processors**; **SuiteCloud Plus** licenses add queues/processors.
- Security = **least privilege**: minimally required role; Script Deployment **Audience**, **Execute as Role**, **Available without Login**; manage credentials with **`N/credentials`**; **`N/crypto`** to encrypt/decipher.
- Never log sensitive data (server or **client-side** logging).

## Practice questions
**Q1 ⭐** Which N/ module offloads a long-running process from a User Event script into a scheduled script?
A) N/cache B) **N/task** C) N/render D) N/redirect — **B**.

**Q2 ⭐** A Sales Order has 8 User Event scripts (5 are yours); saving takes ~1 min. Lowest-impact fix?
A) Move your 5 to the top B) **Consolidate the 5 into 1** C) Undeploy 2 of yours D) Undeploy the other 3 — **B**. Fewer scripts = fewer executions per save, without losing functionality.

**Q3 ⭐** Which SuiteScript module encrypts and deciphers values?
A) N/https B) N/auth C) **N/crypto** D) N/decode — **C**.

**Q4** You need a few values that many script executions reuse, without re-querying each time. Which module?
A) N/task B) **N/cache** C) N/record D) N/format — **B**. `N/cache` stores computed/retrieved data for reuse across executions.

**Q5** Best way to keep a script from running when it isn't needed, improving overall performance?
A) Increase max attempts B) **Filter by execution context and event type** C) Raise the buffer size D) Run as Administrator — **B**. Context/event filtering avoids needless executions.

**Q6** A Suitelet must be reachable by external users who are not logged in. Which Script Deployment setting enables this?
A) Execute as Role = Administrator B) **Available Without Login** C) Audience = All Roles D) Status = Testing — **B**. (Then scope permissions tightly — least privilege still applies.)

> Performance mantra: **fewer executions, right API, offload the heavy stuff.** Security mantra: **least privilege + never log secrets + N/crypto for encryption.**
