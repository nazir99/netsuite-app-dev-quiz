---
type: resource
status: active
created: 2026-07-15
author: ai
---

# NAD - SuiteFlow

Point-and-click automation. Part of [[NetSuite App Dev Hub]].

## The story
A purchase order needs approval. You model it as a **workflow**: boxes are **States** ("Pending Approval", "Approved", "Rejected"), and the record lives in exactly one state at a time. Inside a state, **Actions** do things — set a field, send an email, show a **workflow button**, lock the record. **Transitions** are the arrows: they move the record to the next state, either automatically (on a trigger, when a **condition** is true) or when someone clicks a button. The tricky part is *when* things fire. Triggers run at points in the record lifecycle — some **client-side** (Before Field Edit, Before User Edit/Submit, as the user works in the browser) and some **server-side** (Before Record Load, Before/After Record Submit). A **Confirm** action can only run client-side. And a subtle gotcha: if a state has two outgoing transitions both firing on the *same* button with no distinguishing condition, the workflow simply takes **whichever transition is listed first** — order matters.

## Key facts
- **State → Actions → Transitions.** A record is in one state at a time; transitions move it between states.
- **Triggers:** client (Before Field Edit, Before User Edit, Before User Submit) vs server (Before Record Load, Before Record Submit, After Record Submit) + **Scheduled** and **Entry/Exit** on states/transitions.
- On entering a state, **Entry** actions run first.
- **Confirm action**: client trigger only; fires in **Edit mode on Save**; supports Before Field Edit / Before User Submit triggers.
- Ambiguous transitions on one button → workflow takes the one **listed first** on the Transition subtab.
- A **Saved Search** shows in a workflow's filter dropdown only if it's built on the **same record type** and has proper **Criteria** configured.
- Approval patterns use **buttons + record locking**; "Do Not Exit Workflow" keeps the record in-state.
- Optimize: split client vs server logic, use workflows-initiated-by-workflows, watch the **Workflow Execution Log**.

## Practice questions
**Q1 ⭐** A Saved Search created for a scheduled workflow doesn't appear in the Saved Search filter dropdown. Why? (Choose 2)
A) Execute-as-Admin unchecked B) Search not built on the same record type C) No filter under Available Filters D) No filter set under Criteria subtab E) Public unchecked — **B, D**.

**Q2 ⭐** Which two statements about the **Confirm** action are true? (Choose 2)
A) Only supports Client Triggers B) Executes on any standard button C) Executes on custom workflow buttons D) Executes in View mode E) Executes only in Edit mode on Save — **A, E**.

**Q3 ⭐** State 1 has two transitions to State 2 and State 3, both on the same Add-Button click, no conditions. What happens on click?
A) Goes to 2 then 3 B) Stays in State 1 C) **Transitions to the state listed first under the Transition subtab** D) User picks — **C**.

**Q4 ⭐** Which trigger's actions execute **first** as the record transitions to another state?
A) Before Record Load B) Before User Edit C) **Entry** D) Scheduled — **C**.

**Q5 ⭐** Which two triggers support the **Confirm** workflow action?
A) Before Field Edit B) Before Record Load C) Before Record Submit D) Before User Submit — **A, D**. (Both are client-side; Confirm can't run server-side.)

**Q6** A workflow action must run only on the server, after the record is committed to the database. Which trigger?
A) Before User Edit B) Before Field Edit C) **After Record Submit** D) Before User Submit — **C**. After Record Submit is server-side and post-commit; the others are client-side.

> Mental model for every trigger question: is this **client (browser, before save)** or **server (before/after the DB write)**? That split answers most SuiteFlow items.
