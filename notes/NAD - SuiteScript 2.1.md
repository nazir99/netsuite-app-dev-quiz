---
type: resource
status: active
created: 2026-07-15
author: ai
---

# NAD - SuiteScript 2.1

Biggest slice of the exam. Part of [[NetSuite App Dev Hub]].

## The story
Picture a sales order moving through your account. As the user *opens* the form, a **Client script** wakes up (`pageInit`); as they type, `fieldChanged` and `sublistChanged` fire — all in the browser. They hit Save, and `saveRecord` (client) validates one last time before the record leaves. On the server, a **User Event** script takes over: `beforeLoad` (as the record loads), `beforeSubmit` (before it's written), `afterSubmit` (after it's committed). Need to touch 50,000 records overnight? That job is too big for a Client or User Event script — hand it to a **Map/Reduce** script, which chops the work into pieces and *yields governance between stages*. Need a custom page or an external system to call in? **Suitelet** (renders UI / handles HTTP) or **RESTlet** (JSON API endpoint). Every script type has its own **entry points** — knowing which entry point belongs to which type, and which runs client vs server, is half this exam.

## Key facts
- **Client** (browser): `pageInit, fieldChanged, postSourcing, sublistChanged, lineInit, validateField, validateLine, saveRecord`. `N/currentRecord` is passed in context — **no explicit load needed**.
- **User Event** (server, tied to a record): `beforeLoad, beforeSubmit, afterSubmit`. Has `newRecord`/`oldRecord` in context — **don't re-load the record** in `afterSubmit`.
- **Scheduled** vs **Map/Reduce**: Map/Reduce for large/parallel data sets; stages = `getInputData → map → reduce → summarize`; survives interruptions via `retryCount` + `exitOnError`.
- **Suitelet** = server-side UI/HTTP page (`N/ui/serverWidget`). **RESTlet** = JSON endpoint (GET/POST/PUT/DELETE).
- Retrieve data cheaply: `search.lookupFields()` for a few body fields; `record.load()` only when you need the whole record. `N/query`/SuiteQL for complex joins (SuiteQL supports **Oracle SQL + SQL-92**).
- `N/http`/`N/https` support **GET, POST, PUT, DELETE** (not PATCH). Comms: `N/email, N/http(s), N/sftp`.
- Environment awareness: `N/runtime` (script/session/user settings, feature checks, script params), `N/config`. i18n: `N/currency, N/format` (+ `N/format/i18n`), `N/translation`, `N/recordContext`.
- **Script execution logs are purged every 30 days.**

## Practice questions
**Q1 ⭐** At what interval does NetSuite purge script execution logs?
A) 30 days B) 60 C) 90 D) 120 — **A**. Logs are retained 30 days, then purged.

**Q2 ⭐** Which module does **not** need to be explicitly loaded in an entry-point Client script?
A) N/record B) N/search C) N/runtime D) N/currentRecord — **D**. The current record is passed via the entry-point `context`.

**Q3 ⭐** Most efficient way to retrieve a few body-field values from a record, governance in mind?
A) search.load B) record.load C) `search.lookupFields(options)` D) record.submitFields — **C**. `lookupFields` costs far fewer units than loading the whole record.

**Q4 ⭐** Which HTTP method is **NOT** supported by `N/http` and `N/https`?
A) GET B) PUT C) PATCH D) DELETE — **C**. PATCH is unsupported.

**Q5 ⭐** A Map/Reduce script can be interrupted mid-run. How do you handle interruptions? (Choose 2)
A) try/catch B) set `retryCount` C) configure buffer size D) set `exitOnError` E) "Submit All Stages at once" — **B, D**.

**Q6 ⭐** A developer needs both client- and server-side validation of the same change. Best entry-point / script-type combo?
A) afterSubmit(client)+saveRecord(UE) B) validateField+validateInsert C) `sublistChanged`(Client) + `beforeSubmit`(UE) D) beforeLoad(Client)+pageInit(UE) — **C**. Client `sublistChanged` catches line edits in the browser; UE `beforeSubmit` is the last server-side gate before write. (A, B, D pair entry points with the wrong script type.)

> Drill until you can name every entry point for every script type from memory — that pattern-match is tested repeatedly.
