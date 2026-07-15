---
type: resource
status: active
created: 2026-07-15
author: ai
---

# NAD - Question Bank 60

60 fresh practice questions (no repeats from the official sample), weighted like the real 60-question exam: SuiteScript ~24, SuiteFlow ~10, SuiteBuilder ~8, SDF ~8, Performance & Security ~10. Answer key at the bottom — cover it and self-test. Part of [[NetSuite App Dev Hub]]. Drill the section notes ([[NAD - SuiteScript 2.1]], [[NAD - SuiteFlow]], [[NAD - SuiteBuilder]], [[NAD - SDF]], [[NAD - Performance and Security]]) alongside this.

## SuiteScript 2.1 (Q1–24)
1. Which script type uses the `onRequest` entry point? A) RESTlet B) Suitelet C) Portlet D) Scheduled
2. What are the RESTlet entry points? A) onRequest B) get/post/put/delete C) execute D) render
3. Which entry point does a Scheduled script use? A) execute B) onAction C) each D) onRequest
4. Map/Reduce stages, in order? A) map→reduce→getInputData→summarize B) getInputData→map→reduce→summarize C) getInputData→reduce→map→summarize D) map→getInputData→summarize→reduce
5. Which JSDoc tag declares the script type? A) @NApiVersion B) @NModuleScope C) @NScriptType D) @NAmdConfig
6. What `@NApiVersion` value selects SuiteScript 2.1? A) 2.0 B) 2.x C) 2.1 D) 2
7. On a select field, how do `setValue` and `setText` differ? A) identical B) setValue=internal id, setText=display text C) setText=internal id D) setValue only works client-side
8. Which record mode requires `selectNewLine`/`commitLine` to add sublist lines sequentially? A) standard mode B) dynamic mode C) read-only D) inline
9. Most efficient way to update two body fields **without loading** the record? A) record.load then save B) record.submitFields C) search.lookupFields D) record.copy
10. Read a few field values **without loading** the record? A) record.load B) record.transform C) search.lookupFields D) record.save
11. `search.run().each()` processes up to how many results? A) 1,000 B) 4,000 C) 10,000 D) unlimited
12. Which module checks whether an account feature is enabled? A) N/config B) N/runtime C) N/record D) N/format
13. Which module redirects a user to a record or Suitelet from a server script? A) N/url B) N/redirect C) N/http D) N/task
14. Best client entry point to reject an invalid value for a single field? A) pageInit B) saveRecord C) validateField D) lineInit
15. Which User Event entry point adds buttons/fields to the form as it loads? A) beforeLoad B) beforeSubmit C) afterSubmit D) pageInit
16. Validation that must **block the save** on the server belongs in which UE entry point? A) beforeLoad B) beforeSubmit C) afterSubmit D) fieldChanged
17. Which `UserEventType` indicates a brand-new record being created? A) EDIT B) XEDIT C) CREATE D) COPY
18. Which N/task type submits a Map/Reduce script to run? A) ScheduledScriptTask B) MapReduceScriptTask C) SearchTask D) CsvImportTask
19. Which module sends transactional email with attachments? A) N/http B) N/email C) N/sftp D) N/render
20. Which module/method turns a Sales Order into an Invoice? A) record.copy B) record.transform C) record.create D) record.load
21. Which method runs a SuiteQL statement? A) search.create B) query.runSuiteQL C) record.load D) search.lookupFields
22. Which two HTTP-capable modules can call an external endpoint? (Choose 2) A) N/http B) N/https C) N/url D) N/redirect
23. Which module formats/parses values for a specific locale? A) N/currency B) N/format/i18n C) N/translation D) N/config
24. In a Client script, how do you access the record the user is editing? A) record.load B) N/currentRecord (from context) C) search.lookupFields D) record.copy

## SuiteFlow (Q25–34)
25. Which action runs custom logic beyond the standard action set? A) Set Field Value B) Custom action (Workflow Action Script) C) Go To Record D) Confirm
26. Entry point of a Workflow Action Script? A) onRequest B) onAction C) execute D) each
27. Which action prevents users from editing a record during approval? A) Lock Record B) Set Field Display C) Return User Error D) Confirm
28. A value that must persist across **all** states of a workflow is stored in a…? A) State field B) Workflow field C) Transition D) Custom column field
29. Which trigger runs on the **server**, before the record is written to the database? A) Before Field Edit B) Before User Edit C) Before Record Submit D) After Sourcing
30. Which action returns a blocking error message and stops the save? A) Show Message B) Return User Error C) Send Email D) Confirm
31. To present a custom button the user clicks to move the workflow forward, use…? A) Add Button B) Go To Page C) Set Field Mandatory D) Transform Record
32. Two valid ways to initiate a workflow? (Choose 2) A) Event Based B) Scheduled C) RESTlet D) CSV-only
33. Where do you investigate why a workflow action fired (or didn't)? A) Script Deployment log B) Workflow Execution Log C) Login Audit Trail D) SuiteApp Marketplace
34. Which trigger's actions run **first** when a record enters a new state? A) Exit B) Entry C) After Record Submit D) Scheduled

## SuiteBuilder (Q35–42)
35. Which `N/render` approach injects saved-search results into a template? A) render.transaction B) render.create() + addSearchResults C) render.bom D) render.statement
36. FreeMarker conditional syntax? A) `{{#if}}` B) `<#if condition>…</#if>` C) `[if]…[/if]` D) `<%if%>`
37. Which method produces a PDF file object from a rendered template? A) renderAsString B) renderAsPdf C) toJSON D) save
38. Which template/print engine converts the HTML into the final PDF? A) FreeMarker B) BFO C) BeanShell D) Velocity
39. Which custom object classifies transactions **and** their GL impact lines across many record types? A) custom field B) custom list C) custom segment D) custom record
40. A List/Record field should show only values tied to the selected customer. Configure via…? A) Store Value B) Sourcing & Filtering C) Show in List D) Validation & Defaulting
41. Unchecking **Store Value** on a custom field means…? A) it's required B) the value isn't persisted; it displays/sources at runtime C) it can't be scripted D) it becomes a GL account
42. Which printing approach supports FreeMarker + `N/render` scripting? A) Basic printing B) Advanced PDF/HTML Templates C) Word merge D) Email-only

## SDF (Q43–50)
43. Which file specifies **which** objects and files are deployed? A) manifest.xml B) deploy.xml C) locking.xml D) suitecloud.config.js
44. Which file declares the project type and framework version? A) deploy.xml B) manifest.xml C) hiding.xml D) overwrite.xml
45. Which project type can be **packaged and distributed** to multiple accounts? A) Account Customization B) SuiteApp C) Bundle-only D) RESTlet project
46. Which SuiteCloud CLI (Node.js) command authenticates an account? A) project:deploy B) account:setup C) object:import D) project:validate
47. Which command checks the project for errors **before** deploying? A) project:validate B) project:deploy C) file:import D) object:list
48. Which command pulls existing account objects into your project? A) object:import B) project:package C) project:create D) file:upload
49. `locking.xml`, `hiding.xml`, `overwrite.xml` live in which folder — and which project type? A) Objects / any B) InstallationPreferences / SuiteApp only C) FileCabinet / ACP only D) root / any
50. Which SuiteApp-only CLI command bundles the project for distribution? A) project:deploy B) project:package C) account:setup D) object:import

## Performance & Security (Q51–60)
51. Governance unit limit for a **Scheduled** script? A) 1,000 B) 5,000 C) 10,000 D) unlimited
52. Governance limit for a **User Event / Suitelet / Client** script? A) 1,000 B) 5,000 C) 10,000 D) 100
53. Governance limit for a **RESTlet**? A) 1,000 B) 5,000 C) 10,000 D) 4,000
54. A key performance benefit of Map/Reduce for large data sets? A) runs only client-side B) yields governance between stages and can process in parallel C) never logs D) ignores usage units
55. Which module caches reusable data across executions to cut redundant queries? A) N/task B) N/cache C) N/format D) N/record
56. What governs how many RESTlet requests run in parallel? A) Script status B) Integration concurrency limit / SuiteCloud Processors (SuiteCloud Plus) C) Store Value D) Audience
57. Which Script Deployment setting controls **which roles** the script runs for? A) Execute as Role B) Audience C) Status D) Log Level
58. Which setting runs the deployment under a **specific role's permissions**? A) Audience B) Execute as Role C) Available Without Login D) Deployment ID
59. Where should integration secrets be stored so they aren't hardcoded or logged? A) a plain custom text field B) N/credentials (Credential field) C) script parameters as text D) the execution log
60. Best **first** step to speed up a record that saves slowly due to many User Event scripts? A) raise governance B) consolidate your own UE scripts and filter by context/event type C) move scripts to the top of the list D) run as Administrator

---

## Answer key
1-B · 2-B · 3-A · 4-B · 5-C · 6-C · 7-B · 8-B · 9-B · 10-C · 11-B · 12-B · 13-B · 14-C · 15-A · 16-B · 17-C · 18-B · 19-B · 20-B · 21-B · 22-A,B · 23-B · 24-B
25-B · 26-B · 27-A · 28-B · 29-C · 30-B · 31-A · 32-A,B · 33-B · 34-B
35-B · 36-B · 37-B · 38-B · 39-C · 40-B · 41-B · 42-B
43-B · 44-B · 45-B · 46-B · 47-A · 48-A · 49-B · 50-B
51-C · 52-A · 53-B · 54-B · 55-B · 56-B · 57-B · 58-B · 59-B · 60-B

### Notes on the tricky ones
- **Q9 vs Q10:** `submitFields` **writes** a few body fields without loading; `lookupFields` **reads** them. Both skip the expensive `record.load`.
- **Q11:** `search.run().each()` caps at **4,000** results — use `runPaged()`/`getRange()` beyond that.
- **Q28:** *Workflow field* persists across every state; a *State field* exists only within one state.
- **Q49:** locking/hiding/overwrite are **SuiteApp-only** InstallationPreferences — a repeat of the concept behind official sample Q19/Q20, because it's a favorite exam trap.
- **Q51–53:** memorize the ceilings — Scheduled/Map-Reduce **10,000**, RESTlet **5,000**, everything else (Client/UE/Suitelet/Portlet) **1,000**.
