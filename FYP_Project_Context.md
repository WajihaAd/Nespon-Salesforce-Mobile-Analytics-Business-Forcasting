# FYP Project Context — Salesforce Mobile Business Analytics & Forecasting Application

_Last updated: 19 October 2026, updated with the user-reported Nespon communication._

## 1. Academic and project background

- Student: Muhammad Abdullah Kidwai, final-year BS Data Science student at NED University of Engineering and Technology.
- FYDP/FYP: **Salesforce Mobile Business Analytics & Forecasting Application**.
- Industrial collaborator: **Nespon Solutions**.
- The current FYP is the Salesforce project. HIVE is an older, separate side project and must not be mixed into this FYP unless explicitly requested.
- Main responsibilities: BRD, PRD, User Stories and Acceptance Criteria, project planning/Gantt, supporting project documentation, and requirements traceability.
- Team: Fizza Ahmed (DT-23304, Group Leader); Wajiha Adnan (DT-23001); Taaha Nadeem (DT-23303); Muhammad Abdullah Kidwai (DT-23302).
- Supervisor: Dr. Muhammad Imran. Co-Supervisor: Muhammad Hammad. Industrial Advisor: Kauser Laiq, Developer at Nespon Solutions.

## 2. Authoritative sources and conflict handling

The ZIP `FYP_Salesforce.zip` contains the authoritative project documents. Source-of-truth order:

1. Confirmed Nespon requirements / RBAC Matrix
2. Finalized PRD
3. Finalized BRD
4. Final submitted proposal

If sources conflict, identify the conflict explicitly; do not silently choose or invent a resolution. If the ZIP or documents are supplied in a Work chat, inspect them before doing document-dependent work. Do not claim to have inspected inaccessible files.

The final Gantt chart most recently supplied by the user supersedes the Gantt in the ZIP where dates differ. A schedule transcription is saved separately as `FYP_Final_Gantt_Reference.md`.

## 3. Critical scope boundary

Although “Forecasting” appears in the project title, forecasting is a **future enhancement and out of scope for current implementation**. Do not add forecasting models, predictive forecasting, forecast rollups, or forecast implementation tasks unless Muhammad explicitly approves a scope change.

Current focus: mobile Salesforce access, business analytics, KPI dashboards, lead and opportunity visibility, notifications, automation, role-based security, testing/evaluation, and documentation.

## 4. Project overview

This is a mobile-first Salesforce business analytics and decision-support application. Salesforce already provides CRM functionality; the project is not a replacement CRM. It aims to help sales and business users access Salesforce information on mobile devices, monitor performance, analyze leads and opportunities, view KPIs, and make timely decisions.

Business problems:
- Limited convenience accessing business information on mobile devices.
- Difficulty monitoring sales performance and KPIs.
- Limited visibility into leads and opportunities away from a desktop.
- Delayed access to relevant business insights.
- Need for timely alerts and follow-up reminders.
- Role-specific requirements for secure data visibility.

Functional areas:
1. Mobile access to Salesforce information.
2. Lead management and lead-conversion visibility.
3. Opportunity management and pipeline monitoring.
4. Business analytics and KPI dashboards.
5. Filtering and drill-down into relevant business information.
6. Notifications and automation using Salesforce Flows.
7. Role-based access control and data security.
8. Testing, evaluation, and documentation.

## 5. Salesforce implementation approach

Use a configuration-first, declarative approach wherever possible.

Preferred features:
- Confirmed core standard objects: Account, Contact, Lead, and Opportunity. Nespon has explicitly confirmed proceeding with the currently selected objects.
- Custom fields where required.
- Salesforce Reports and Dashboards.
- Lightning Pages.
- Salesforce Flows.
- Native Salesforce security/access controls.

Use Apex only if native configuration cannot meet a confirmed requirement. New custom objects are generally out of scope, except for documented BR-08 when a required business entity genuinely cannot be represented by standard objects. Do not assume a Salesforce edition, license, external API, Einstein feature, third-party service, or integration is available unless finalized documents or confirmed Nespon requirements establish it.

Use sample/demo data. Do not place confidential Nespon client data in the development org. Historical sales, revenue, lead, and opportunity data is required where appropriate for meaningful analytics and trends.

## 6. Confirmed user roles and security rules

Seven roles:
1. Sales Representative
2. Sales Manager
3. Sales Ops / RevOps Analyst
4. VP Sales / Executive
5. Executive Viewer (Board/C-Suite)
6. System Administrator
7. Integration / API User

Use native Salesforce controls according to the finalized RBAC Matrix and requirements: profiles, Permission Set Groups (PSGs), Role Hierarchy, Sharing Rules, report/dashboard folder security, and Field-Level Security (FLS). Do not invent additional permissions.

Rules:
- Executive Viewer: view-only access to curated executive dashboards; no direct object access.
- Integration / API User: API access, not Salesforce Mobile App UI access.
- Protect quota and commission fields with FLS.
- Executive dashboards use a dedicated running user so organization-wide totals are not unintentionally clipped by viewer access.
- Users without required permission assignments must not receive unauthorized access.
- Errors must not disclose restricted information.

## 7. Confirmed KPI and dashboard scope

KPIs: Total Leads, Lead Conversion, Total Sales, Revenue, Opportunities/Pipeline, Target Achievement, and Growth.

Dashboards should provide role-appropriate information, date filters, and applicable salesperson or region filters. Do not invent exact KPI formulas, targets, fields, or calculation rules when documents do not define them; flag gaps for clarification.

## 8. Notifications and automation

Confirmed events:
- New lead created.
- Opportunity updated or stage changed.
- Sales target missed or achieved.
- Follow-up due.
- Opportunity closing date approaching.
- Navigation from notification to the relevant record, subject to user permissions.

Use Salesforce Flows where suitable. Follow the finalized PRD for exact triggers, recipients, and expected behavior. Do not assume an unapproved external notification service.

## 9. User stories and traceability

The finalized User Stories document contains 47 stories, US-01 through US-47, with acceptance criteria and a traceability matrix linking Business Requirements → Functional Requirements → User Stories → Acceptance Criteria.

Major epics:
1. Mobile Access
2. Lead Management
3. Opportunity Management
4. Business Analytics
5. KPI Dashboards
6. Notifications & Automation
7. Forecasting — Future Enhancements / Out of Scope
8. Role-Based Access & Security
9. Other Confirmed Project Functionality

Preserve existing IDs and traceability when revising or extending documents; do not unnecessarily renumber finalized requirements. User-story format: “As a [role], I want [capability], so that [benefit].” Acceptance criteria must be testable and unambiguous.

## 10. Edge cases and constraints

- Empty states when no leads, opportunities, or relevant data exist.
- Deny unauthorized actions.
- Invalid dashboard-filter combinations must not produce misleading results.
- No custom offline mode; standard Salesforce Mobile App offline behavior applies.
- Integration/API User has no Mobile App UI by design.
- Unauthorized errors must not expose restricted information.
- Users without assigned PSGs or appropriate Role Hierarchy positions are treated as having no access until properly assigned.

## 11. Project planning and Gantt requirements

Derive tasks from the finalized BRD, PRD, and User Stories. Include realistic dependencies and milestones. Cover requirements analysis, Salesforce configuration, analytics, dashboards, notifications, security, testing, evaluation, deployment, and documentation where applicable. Do not blindly copy a generic SDLC, add forecasting implementation, or invent NED deadlines, assessment/submission dates, completion percentages, or durations. Ask for the actual academic timeline if unavailable. Distinguish confirmed deadlines from proposed planning dates. Model dependencies, not just a list of tasks.

Potential outputs: work breakdown structure, task IDs, duration, start/end dates, dependencies, milestones, responsibilities, deliverables, Gantt chart—include only fields supported by available information.

## 12. Documentation quality

Project documents should read like genuine university FYDP documentation for an industry collaboration: professional, consistent, specific, and technically credible; no generic filler or repetition. Maintain consistency across proposal, BRD, PRD, User Stories, design, implementation, testing, and plan.

Distinguish **Confirmed**, **Proposed**, **Pending Clarification**, and **Assumption**. Never invent requirements, technologies, datasets, APIs, licenses, stakeholders, features, or deadlines. Preserve finalized requirements unless Muhammad explicitly requests a change. Flag contradictions and missing information.

## 13. Academic value

Describe the project as combining Business Analytics, Data Analytics, Data Visualization, Mobile Computing, Salesforce/CRM, Enterprise Systems, API Integration where confirmed, Software Engineering, and Decision Support. Do not reduce it to “Salesforce configuration.”

## 14. Work-mode preferences

1. Understand the request and inspect relevant finalized documents first.
2. Use exact project details and requirement IDs when available.
3. Give beginner-friendly, step-by-step implementation instructions.
4. For requested files/deliverables, create complete usable artifacts rather than only describing them.
5. Preserve existing content and structure when editing unless change is necessary.
6. Verify calculations, dependencies, dates, references, and generated files before delivery.
7. Do not claim a file was created, inspected, tested, or verified unless that actually happened.
8. If essential information is missing, ask a focused question or mark the assumption.
9. Keep explanations clear and practical without unnecessary repetition.
10. Forecasting remains a future enhancement, not current implementation scope.

## 15. Current Team Work Allocation (reported 17 October 2026)

For the upcoming Monday, 19 October 2026:
- Muhammad Abdullah Kidwai and Taaha Nadeem: Salesforce Architecture.
- Fizza Ahmed and Wajiha Adnan: Security and RBAC.

Treat this as the team's current reported work split, not as an approved change to requirements or scope. Align architecture and security work with the finalized project documents and Gantt baseline.
## 16. Latest Nespon communication (reported 19 October 2026)

The user shared the following latest exchange with Nespon Solutions. Treat these as user-reported confirmations, not independently verified statements:

- Muhammad asked whether the currently selected Salesforce objects should proceed or be changed after Nespon's review. Nespon replied: **“Yes please proceed with the current objects.”** The four confirmed core objects remain **Account, Contact, Lead, and Opportunity**; do not change this selection based on that review.
- Muhammad asked for an update on a previously discussed data-fetching issue. Nespon replied: **“Please use this sockle to fetch data.”** The word “sockle” is unclear and may be a transcription/typing error for “SOQL,” but that interpretation is **not confirmed**. Record SOQL as a likely interpretation pending clarification, not as an exact confirmed instruction.
- Muhammad shared the account identifier `fizza.ahmed_crm_analytics@nespon.demo`. Nespon later replied: **“Please check again. your account is working fine.”** This indicates Nespon reported the account was working; it does not by itself establish that the data-fetching issue was resolved.
- A document was referenced: `Salesforce Role Hierarchy – Trailhead List.docx`. Nespon's reported direction was to log into Trailhead and open the links provided in that document. The document's contents have not been inspected in this update; inspect the actual file before relying on its links or treating its contents as project requirements.

For any follow-up on data fetching, keep the distinction clear: account functionality was reported as working, while the exact fetching method and resolution status remain to be verified. Do not request or store passwords, session cookies, or access tokens.
