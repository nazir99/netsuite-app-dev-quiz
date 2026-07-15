---
type: resource
status: active
created: 2026-07-15
author: ai
---

# NAD - SuiteBuilder

Customization + printouts. Part of [[NetSuite App Dev Hub]].

## The story
Finance wants the invoice PDF to show the line items in a clean table, break to a new page after the terms, and print dates the customer's way. That printout is an **Advanced PDF/HTML Template**: NetSuite feeds record data into a **FreeMarker** template, then the **BFO** engine turns the HTML into a PDF. FreeMarker is the loop-and-format language — `<#list record.item as item>…</#list>` walks the sublist, `${item.amount}` prints a field, and `<pbr/>` forces a page break. From SuiteScript you can drive the same engine with **`N/render`** (`render.transaction`) to generate the PDF programmatically. Separately, SuiteBuilder is where you build the data model itself: **custom fields** (with Sourcing & Filtering, Validation & Defaulting, Store Value), **custom records**, and **custom segments** — the segment being the powerful one because it classifies transactions *and their GL lines* across many record types, with built-in filtering by subsidiary. Every customization has security and performance weight: unchecking **Store Value** means the field isn't persisted, and deleting a custom record type can strand data and GL impact.

## Key facts
- **Advanced PDF/HTML** pipeline: record data → **FreeMarker** template → **BFO** renderer → PDF.
- FreeMarker: `<#list list as item>…</#list>` to iterate sublists; `${field}` to output; supports record joins, field labels, date/number formatting (locale-aware).
- Page break tag = **`<pbr/>`**.
- Script-driven rendering = **`N/render`** (e.g. `render.transaction`, `render.create`), using standard or custom data sources.
- **Custom field** options: **Store Value** (persist vs display-only), **Show in List**, **Sourcing & Filtering** (auto-fill from a related record; filter a List/Record field by another field), **Validation & Defaulting**.
- **Custom segment** > custom field when you need cross-record classification with GL-line impact and subsidiary/filtering built in.
- Security: custom field/record access is role-driven; sourcing & filtering interact with permissions; inactivating/deleting custom record types can break data and GL.

## Practice questions
**Q1 ⭐** Which tag adds a page break in an Advanced PDF template?
A) `<br/>` B) `<pbr/>` C) `<page-break/>` D) `<nxt-pge/>` — **B**.

**Q2 ⭐** The current day value must be converted to a string and stored in a custom field. Which formula?
A) `TO_DATE({trandate},'DAY')` B) `TO_CHAR({trandate},'DAY')` C) `TO_STRING({today},'DAY')` D) `TRUNC({today},'DD')` — **B**. `TO_CHAR` with the `DAY` format converts a date to its text day-name.

**Q3** Which SuiteScript module renders a transaction record to a PDF?
A) N/ui B) **N/render** C) N/format D) N/file — **B**. `render.transaction()` drives the FreeMarker/BFO engine from script.

**Q4** In a FreeMarker template, which syntax iterates the line items of a transaction?
A) `<#for item in items>` B) `<#each record.item>` C) `<#list record.item as item>…</#list>` D) `{{#items}}` — **C**. FreeMarker uses `<#list … as …>`.

**Q5** A custom field has **Store Value** unchecked. What is the effect?
A) The field is required B) **The value is not persisted on the record — it only displays/sources at runtime** C) The field can't be scripted D) It becomes a GL field — **B**.

**Q6** You must classify both transactions and their GL impact lines across many record types, with per-subsidiary filtering built in. Which customization?
A) Custom field B) Custom list C) **Custom segment** D) Custom record — **C**. Custom segments are designed for cross-record, GL-aware classification.

> When a question mentions printouts/emails, think **FreeMarker + BFO + `<pbr/>` + N/render**. When it mentions the data model, think **field vs record vs segment** and their **Store Value / sourcing / security** implications.
