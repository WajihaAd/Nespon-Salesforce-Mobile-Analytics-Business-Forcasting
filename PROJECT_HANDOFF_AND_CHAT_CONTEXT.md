# FYP Salesforce Project — Teammate Handoff

**Prepared:** 23 October 2026  
**Purpose:** Continue the project in a new Codex chat using the decisions and materials below.

## Project and people

- **Project:** Salesforce Mobile Business Analytics & Forecasting Application (FYDP/FYP), BS Data Science, NED University of Engineering and Technology; industrial collaborator: Nespon Solutions.
- **Team:** Fizza Ahmed (DT-23304, group leader); Wajiha Adnan (DT-23001); Taaha Nadeem (DT-23303); Muhammad Abdullah Kidwai (DT-23302).
- **Supervisors:** Dr. Muhammad Imran (supervisor); Muhammad Hammad (co-supervisor); Kauser Laiq (industrial advisor, Nespon Solutions).
- Reported work split: Muhammad and Taaha on Salesforce Architecture; Fizza and Wajiha on Security/RBAC.
- HIVE is an older, separate project and must not be mixed into this FYP.

## Source of truth and working rules

Authoritative priority: (1) confirmed Nespon requirements/RBAC Matrix, (2) finalized PRD, (3) finalized BRD, (4) final submitted proposal. The final user-supplied Gantt chart supersedes older schedules where dates conflict. If sources conflict, call it out; distinguish Confirmed, Proposed, Pending Clarification, and Assumption. Preserve requirement IDs and traceability. Do not invent requirements, formulas, deadlines, licenses, APIs, features, or permissions. Give beginner-friendly steps and create complete deliverables when asked.

The original `FYP_Salesforce.zip` was not found at the checked Desktop path, but its accessible extracted project directory was packaged under `Source_Files`. Some old uploaded files mentioned in conversation may not be in this workspace. Do not claim they were reviewed unless the actual file is present.

## Product scope and architecture

This is a mobile-first Salesforce business analytics and decision-support experience, not a replacement CRM. The intended client is the standard Salesforce Mobile App with mobile-optimized Lightning navigation/pages, not a bespoke Play Store/App Store app.

High-level flow: eligible human role → Salesforce Mobile App → role-appropriate navigation/Lightning pages → standard Salesforce data model (Lead, Account, Contact, Opportunity) → Reports/KPI Dashboards and Flow notifications, with Salesforce checking object, record, field, and folder access at use time.

Use a configuration-first declarative approach: standard objects, custom fields only when required, Salesforce Reports/Dashboards, Lightning Pages, Flows, and native security. Apex only if a confirmed requirement cannot be met declaratively. New custom objects are generally out of scope except the documented BR-08 exception. Use sample/demo data; never put confidential Nespon client data in the development org. Do not assume licenses, edition features, external services, Einstein, or APIs unless source documents/Nespon confirm availability.

## Final core objects and data model

Nespon confirmed proceeding with these four standard objects: **Account, Contact, Lead, Opportunity**. Typical standard relationships discussed: Lead conversion can create/link an Account and Contact, with an Opportunity optional; one Account can have multiple Contacts and Opportunities.

Earlier Schema Builder exploration included `AcquiredAccount__c`, `Reseller_Account_Plan__c`, and an idea called `FYP_Accounts`. These are **not** the final core-object selection. Do not continue building `FYP_Accounts` unless a documented BR-08 requirement and user approval establish the need. The user once supplied CSVs for Account and those custom objects, but those CSVs were not available in Downloads during this handoff build; no claims about column-level selection are made here.

## Functional requirements recalled from the project context

- Mobile Salesforce information access.
- Lead management, follow-up, and conversion visibility.
- Opportunity stage, pipeline, amount, and close-date visibility.
- Accounts and related Contacts.
- Business analytics, role-specific KPI dashboards, filters, and permitted drill-down.
- Salesforce Flow notifications/automation.
- Native RBAC/security; testing, evaluation, and documentation.

Named KPIs: Total Leads, Lead Conversion, Total Sales, Revenue, Opportunities/Pipeline, Target Achievement, Growth. Exact formulas, target sources, fields, and calculation rules must come from finalized docs or Nespon; do not infer them.

Named notification events: new Lead; Opportunity update/stage change; target missed/achieved; follow-up due; closing date approaching. Follow PRD for exact triggers, recipients, and behavior. Notifications should navigate to a record only if the user has access. No unapproved third-party service.

Edge cases: empty states; deny unauthorized actions; invalid filters must not mislead; no custom offline mode; Integration/API user has no mobile UI; errors must not expose restricted information.

## RBAC roles and rules

Seven baseline roles: Sales Representative; Sales Manager; Sales Ops/RevOps Analyst; VP Sales/Executive; Executive Viewer (Board/C-Suite); System Administrator; Integration/API User.

Use profiles, Permission Set Groups, Role Hierarchy, sharing rules, folder access, and Field-Level Security per the RBAC Matrix. Specific constraints: Executive Viewer sees curated executive dashboards only and has no direct object access; Integration/API User uses API and not Mobile App UI; protect quota/commission fields using FLS; executive dashboards need a dedicated running user to preserve org-wide totals; missing permissions mean no access; denied/error messages must not disclose protected data.

## Salesforce org progress (from user screenshots and reported steps)

- Salesforce Developer Edition org shown as `nesponinc3-dev-ed`. Nespon said it is the project org, only the group is working there, and it has a super account with CEO role: **do not change that CEO/super account**.
- Role Hierarchy screens showed these project entries: `VP Sales / Executive` under the organization; `Sales Manager` reporting to VP Sales / Executive; `Sales Representative` reporting to Sales Manager. The org also already showed CEO, CIO, Sales WW, Sales AMER, Sales EMEA. Verify live state before changes; don't treat existing role nodes as new work.
- The other four baseline roles (Sales Ops/RevOps Analyst, Executive Viewer, System Administrator, Integration/API User) need verification/implementation against the RBAC Matrix. Do not assume the entire seven-role RBAC is complete.
- Sharing Settings were changed to: Lead = Private; Account and Contract = Private in Salesforce's combined OWD row; Opportunity = Private; Contact = Controlled by Parent. Role hierarchy access was checked/enabled. User clarified Case was already Private and was not intentionally changed; Case is not a project object. Salesforce warned “Case Access must be Private when the Account Access is set to Private”; case remained Private.
- A user-list screenshot showed a populated demo org and active admin accounts; don't reassign or modify CEO/super account. Verify licenses and actual project users before assigning roles/permission sets.
- Next RBAC work: inspect the actual RBAC Matrix; verify profiles/PSGs, object CRUD, FLS, record-sharing, dashboard/report folder access and assignments; then validate with representative test users. Avoid more org-wide changes until current state is checked against the matrix.

## Gantt baseline

Final user-provided chart spans August 2026–May 2027 at month granularity. `FYP_Final_Gantt_Reference.md` is included. Main flow: literature/review and proposal (Aug–Sep); requirement gathering (Sep–Oct); system design/architecture (Oct–Nov); Salesforce environment/data and security (Nov–Dec); mobile mockup (late Nov–Jan); analytics/KPIs/dashboards (Dec–Jan); Lead/Opportunity (Jan–Feb); notification/automation (Feb–Mar); front end and system integration/function testing (Mar–Apr); mobile usability/performance (Apr–May); documentation/refinement (Feb–May); final demo/evaluation (May). The chart gives no day-level deadlines or exact durations. Do not invent them. Forecasting implementation is not on the current schedule.

## Trailhead and Nespon communication

Trailhead TrailMix supplied: `https://trailhead.salesforce.com/users/q4i16hmbb0jbzim3hb/trailmixes/nespon-salesforce-starter-pack`. Screenshot showed 25% progress and roughly 24 hours remaining; this does not mean the modules were all completed. Nespon asked the user to log in to Trailhead and open links in `Salesforce Role Hierarchy – Trailhead List.docx`; inspect that actual file before following its links.

User-reported Nespon statements: (1) don't change the CEO/super account; this is the group’s project org; (2) proceed with current objects; (3) “Please use this sockle to fetch data.” “sockle” may be a typo/transcription of SOQL but is unconfirmed; (4) Nespon later said the account was working fine. That does not prove the data-fetching issue was resolved. Do not request or store passwords, cookies, or tokens.

## Standee history/current artifact

Earlier editable SVG work targeted 24 × 72 inches and caused Inkscape font/layout trouble. Those versions were superseded. The latest user-supplied final standee is `Source_Files/Standee/FYP_Standee.pdf` from `Desktop\FYP_Salesforce\Standee\FYP_Standee.pdf`. It was verified as one page, 1728 × 4320 pt = **24 × 60 inches**. This supersedes the older 24 × 72 designs. Do not edit or replace the latest standee unless asked.

## Package inventory / limitations

Included in `Source_Files`: three project diagrams; accessible clarification questions, Nespon brief, RBAC Matrix, Trailhead hierarchy links, BRD/PRD/User Stories in available DOCX/PDF forms, logo reference; proposal DOCX/PDF; and the latest standee PDF. Also included: existing master context and Gantt reference. Earlier Account/custom-object CSV exports and the original named `FYP_Salesforce.zip` were not found at the checked paths. Browser profiles/caches and credentials are intentionally excluded.

## Prompt for continuing in a new Codex chat

“Read `PROJECT_HANDOFF_AND_CHAT_CONTEXT.md`, `FYP_Project_Context.md`, `FYP_Final_Gantt_Reference.md`, and the included authoritative BRD, PRD, User Stories, and RBAC Matrix first. Continue Salesforce Architecture/RBAC based on those sources and the org progress recorded in the handoff. Do not modify the CEO/super account. The final objects are Account, Contact, Lead, Opportunity. Forecasting is future scope. Verify current Salesforce configuration before making changes; don't invent permissions, formulas, deadlines, or unavailable data. The latest standee is the included 24 × 60 inch PDF.”
