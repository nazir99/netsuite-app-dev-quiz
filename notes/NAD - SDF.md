---
type: resource
status: active
created: 2026-07-15
author: ai
---

# NAD - SDF (SuiteCloud Development Framework)

Source-controlled dev + deployment. Part of [[NetSuite App Dev Hub]].

## The story
You've built customizations in a sandbox and need to move them to production — reliably, repeatably, from your own machine. That's **SDF**: you keep NetSuite objects and scripts as XML/JS files in a project, version-control them, and push with the **SuiteCloud CLI for Node.js** (or the Java CLI). First decision: **Account Customization Project (ACP)** or **SuiteApp Project?** An ACP deploys to *one specific account* — great for a single customer's tailoring. A SuiteApp is a *distributable, bundled* application you can install into many accounts. That distinction drives what you can do: certain **InstallationPreferences** — locking objects (`locking.xml`), hiding them (`hiding.xml`), overwriting on update (`overwrite.xml`) — live in a SuiteApp project's `InstallationPreferences` folder and are **not available to Account Customization projects**. Two files anchor every project: **`manifest.xml`** (project type, framework version, dependencies) and **`deploy.xml`** (what to deploy). The workflow is always the same rhythm: authenticate the account, then **validate** before you **deploy**.

## Key facts
- **Account Customization Project** → deploys to a single account. **SuiteApp Project** → a distributable bundled app for many accounts.
- **`manifest.xml`**: declares project type, framework version, and dependencies. **`deploy.xml`**: lists objects/files to deploy.
- **`InstallationPreferences`** folder (SuiteApp projects only): `locking.xml`, `hiding.xml`, `overwrite.xml`. **Locking/hiding is NOT supported in Account Customization projects.**
- **SuiteCloud CLI for Node.js** typical sequence: `account:setup` (authenticate) → `project:validate` → `project:deploy`. `object:import` pulls existing account objects into the project; `file:import` for files.
- Objects go in the `Objects` folder; scripts/files in `FileCabinet`. SDF supports a defined set of custom object types (see the SDF reference).
- Debugging deploy failures: read CLI validation output; check dependencies declared in `manifest.xml`.

## Practice questions
**Q1 ⭐** An Account Customization project's `locking.xml` deployed with no errors, but the custom list still shows unlocked. Why?
A) defaultAction should be LOCK B) **Locking objects is not supported in Account Customization projects, only SuiteApp projects** C) Object tag syntax is wrong D) SDF can't lock custom lists — **B**.

**Q2 ⭐** Which XML files must go in the `InstallationPreferences` folder of an SDF **SuiteApp** project? (Choose 3)
A) locking.xml B) hiding.xml C) manifest.xml D) deploy.xml E) overwrite.xml — **A, B, E**. (`manifest.xml` and `deploy.xml` live at the project root, not in InstallationPreferences.)

**Q3** Which project type produces a distributable application installable into multiple accounts?
A) Account Customization Project B) **SuiteApp Project** C) Bundle-only project D) RESTlet project — **B**.

**Q4** Which file declares the project type, framework version, and dependencies?
A) deploy.xml B) **manifest.xml** C) locking.xml D) suitecloud.config.js — **B**.

**Q5** Correct SuiteCloud CLI order to safely push customizations to an account?
A) deploy → validate → setup B) **account:setup → project:validate → project:deploy** C) project:deploy → object:import D) validate → import → setup — **B**. Authenticate, validate, then deploy.

**Q6** You need to bring existing customizations from a NetSuite account into your SDF project as objects. Which command?
A) project:deploy B) **object:import** C) project:validate D) file:upload — **B**.

> Two anchors to memorize: **ACP = one account / SuiteApp = distributable**, and **`manifest.xml` + `deploy.xml` at root; locking/hiding/overwrite only in SuiteApp `InstallationPreferences`.**
