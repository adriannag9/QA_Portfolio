# 🧪 QA Test Plan – OpenEMR Patient Management

> ⚠️ **Note on Context**
> This test plan was created for portfolio purposes using **OpenEMR** — an open-source Electronic Medical Records system available at [openemr.net/demo](https://www.openemr.net/demo).
> All patient data, user accounts, and scenarios described in this document are fictional and used solely for demonstration.
> Internal links (e.g. to Jira, Confluence, Agile Test) are provided for illustrative purposes only and reflect real-world documentation practices.

---

## 📑 Version History

| Version   | Date        | Author         | Reviewer      |
|-----------|-------------|----------------|---------------|
| 0.1-draft | 04 May 2026 | Adrianna Golak |               |
| 1.0       | 04 May 2026 | Adrianna Golak | self-reviewed |

---

## 📑 Table of Contents

1. [🎯 Stakeholders](#-stakeholders)
2. [🔍 Project-Specific Impact to Testing](#-1-project-specific-impact-to-testing)
3. [📦 Scope of Testing](#-2-scope-of-testing)
   - [✅ In Scope](#-21-in-scope)
   - [❌ Out of Scope](#-22-out-of-scope)
   - [🧰 Third-Party Systems](#-23-third-party-systems)
4. [✅ Quality and Acceptance Criteria](#-3-quality-and-acceptance-criteria)
5. [🧪 Test Process Description](#-4-test-process-description)
   - [🔍 Testing Types Overview](#-41-testing-types-overview)
   - [🔍 Testing Types Summary](#-42-testing-types-summary)
   - [📌 Jira Tasks](#-43-jira-tasks)
   - [🐞 Defects & RCA](#-44-defects--rca)
   - [📋 Test Case Management & Execution](#-45-test-case-management--execution)
   - [📊 Test Report Containment](#-46-test-report-containment)
   - [📐 Project Metrics](#-47-list-of-metrics-to-track)
6. [⚠️ Risks and Assumptions](#-5-risks-and-assumptions)
7. [📱 Devices](#-6-devices)
8. [🛠️ Toolset](#-7-toolset)
9. [🌐 Test Environments](#-8-test-environments)
10. [📣 Communication Plan](#-9-communication-plan)
11. [🚨 Escalation Plan](#-10-escalation-plan)
12. [🗓️ Test Schedule](#-11-test-schedule)
13. [🧾 Test Deliverables](#-12-test-deliverables)

---

## 🎯 Stakeholders

| Role | Name | Responsibilities |
|------|------|-----------------|
| QA Engineer | Adrianna Golak | Test planning, test case design, execution, defect reporting, metrics |
| Product Owner (simulated) | — | Acceptance of exit criteria, defect prioritization |
| Development Team (simulated) | — | Bug fixes, environment maintenance |

> In this portfolio context, QA Engineer acts as the sole responsible party for all testing activities.

---

## 🔍 1. Project-Specific Impact to Testing

- **Goal:** Validate core patient management and clinical workflows in OpenEMR across web, mobile, and API layers to ensure system reliability, data integrity, and usability.
- **Tech stack:** PHP-based web application, MySQL database, REST API.
- **Current phase:** Functional testing of core features across multiple test types: manual (web & mobile), API, regression, and usability.
- **Testing approach:** Risk-based manual testing — priority given to workflows with direct impact on patient data, system access, and cross-platform consistency.
- **Key challenge:** OpenEMR is a complex, domain-specific system with a steep learning curve. Understanding the clinical workflows is a prerequisite to testing them effectively. Additionally, the responsive web view used on mobile introduces a separate layer of platform-specific risks.

---

## 📦 2. Scope of Testing

### ✅ 2.1 In Scope

| Module | Description | Test Types | Responsible |
|--------|-------------|-----------|-------------|
| 🟢 **Patient Registration** | Creating, editing and retrieving patient records; required field validation | Manual (Web + Mobile), API, Regression | QA Engineer |
| 📅 **Appointment Scheduling** | Booking, editing, cancelling appointments; conflict detection; calendar accuracy | Manual (Web + Mobile), Regression, Usability | QA Engineer |
| 💊 **Prescription Management** | Creating prescriptions; mandatory field validation; prescription history | Manual (Web), API, Regression | QA Engineer |
| 🔐 **User Roles & Access Control** | Permissions per role: Admin, Physician, Nurse, Receptionist | Manual (Web), API, Regression | QA Engineer |
| 🗂️ **Medical Records** | Creating, editing, viewing documents linked to patient profiles | Manual (Web + Mobile), Regression | QA Engineer |
| 🔍 **Patient Search** | Search by name, ID, date of birth; results accuracy | Manual (Web + Mobile), API, Usability | QA Engineer |
| 🌐 **API Layer** | REST API endpoints for patient, appointment and prescription data | API Testing (Postman + HTTP Toolkit) | QA Engineer |
| 📱 **Mobile Web** | Responsive web experience on iOS and Android devices | Manual (Mobile), Usability | QA Engineer |

### ❌ 2.2 Out of Scope

| Component | Reason |
|-----------|--------|
| Automated test execution | Manual testing only in this test plan |
| Performance & load testing | Requires dedicated tooling and environment; planned for future cycle |
| Third-party integrations (labs, insurance) | Not available in demo environment |
| Native mobile application | OpenEMR does not provide a dedicated native app |
| Payment and billing module | Excluded from current scope |

### 🧰 2.3 Third-Party Systems

| System | Usage | Responsible |
|--------|-------|-------------|
| OpenEMR Demo Server | Primary test environment | External (openemr.net) |
| Postman | API test execution and collection management | QA Engineer |
| HTTP Toolkit | API traffic interception and inspection | QA Engineer |
| LambdaTest | Cross-browser and cloud mobile device testing | QA Engineer |
| Physical iOS device | Mobile manual and usability testing | QA Engineer |
| Physical Android device | Mobile manual and usability testing | QA Engineer |

---

## ✅ 3. Quality and Acceptance Criteria

- All features listed in Section 2.1 are covered by test cases across applicable test types.
- **No Critical or High severity bugs** remain open at exit.
- Minimum **90% test case pass rate** achieved across all test types.
- All API endpoints in scope return correct status codes and response bodies.
- Mobile web experience is functionally equivalent to desktop for all critical workflows.
- Usability issues are documented and assessed against WCAG 2.1 AA criteria.
- A formal **Test Execution Report** is delivered at the end of the testing cycle.
- Medium and Low severity defects are documented, triaged, and accepted for deferral where applicable.

---

## 🧪 4. Test Process Description

### 🔍 4.1 Testing Types Overview

| 🧪 Test Type | ✍️ Designed By | 🛠️ Tools | 👤 Performed By | 📱 Platform |
|-------------|---------------|----------|----------------|------------|
| Manual Functional Testing – Web | Adrianna Golak | OpenEMR demo, Jira, Agile Test | Adrianna Golak | Desktop: Chrome, Firefox |
| Manual Functional Testing – Mobile | Adrianna Golak | OpenEMR demo, LambdaTest, physical devices | Adrianna Golak | iOS, Android |
| API Testing | Adrianna Golak | Postman, HTTP Toolkit | Adrianna Golak | N/A |
| Usability Testing | Adrianna Golak | OpenEMR demo, physical devices, WCAG 2.1 AA checklist | Adrianna Golak | Web + Mobile |
| Regression Testing | Adrianna Golak | OpenEMR demo, Agile Test | Adrianna Golak | Web + Mobile |
| Role-Based Access Testing | Adrianna Golak | OpenEMR demo, Postman | Adrianna Golak | Web + API |

---

### 🔍 4.2 Testing Types Summary

| 🧪 Test Type | 📝 Description | 📅 Phase | ✅ Completion Criteria | 📊 Expected Results |
|-------------|---------------|---------|----------------------|-------------------|
| Manual Functional – Web | Verification of all in-scope features on desktop browsers | Primary cycle | All web test cases executed; no open Critical/High bugs | Features work as specified on Chrome and Firefox |
| Manual Functional – Mobile | Verification of critical workflows on iOS and Android via responsive web | Parallel to web cycle | All mobile test cases executed; platform-specific defects documented | Core workflows functional and usable on mobile |
| API Testing | Validation of REST API endpoints: correct responses, status codes, error handling, and auth | Dedicated API cycle | All in-scope endpoints tested; Postman collection documented | API returns expected data; unauthorized requests rejected |
| Usability Testing | Evaluation of ease of use, navigation clarity, and WCAG 2.1 AA compliance on web and mobile | Final phase | Usability checklist completed; WCAG audit documented | Issues logged by severity; recommendations provided |
| Regression Testing | Re-execution of core test cases after defect fixes to confirm no new issues introduced | Post-fix cycle | All regression cases re-executed | No regressions; fixed bugs confirmed closed |
| Role-Based Access Testing | Validating that each user role can only access permitted features on UI and API level | Dedicated access cycle | All roles tested; permission matrix covered | Unauthorized actions blocked on UI and API |

---

### 📌 4.3 Jira Tasks

All testing activities are tracked via Jira with the following task types:

- 🧩 **Feature Testing Tasks** — created per module and test type (web / mobile / API)
- 🔄 **Retest Tasks** — triggered after a defect is marked as fixed
- 📂 **Regression Packs** — grouped test runs per regression cycle
- 🐞 **Bug Reports** — raised as separate Jira issues with full defect metadata
- 🌐 **API Test Tasks** — separate task group for Postman collection execution and findings

---

### 🐞 4.4 Defects & RCA

#### 🔄 4.4.1 Defect Lifecycle

```
New → Triaged → In Progress → Ready for Retest → Retest → Closed / Reopened
```

- Severity and priority assigned at triage
- All defects linked to the relevant test case in Agile Test
- Platform tag applied to each bug: `[Web]`, `[Mobile-iOS]`, `[Mobile-Android]`, `[API]`

#### 🧷 4.4.2 Defect Raising Rules

- **In-scope bugs:** Raised within the active test cycle, linked to the relevant feature and platform
- **Out-of-scope bugs:** Logged separately with full impact analysis; marked for future cycle
- Each bug report must include: steps to reproduce, expected vs actual result, severity, priority, environment, platform, and attachments (screenshots / Postman response)

#### 🧠 4.4.3 Root Cause Analysis (RCA)

Performed for Critical and High severity defects:

1. Identify when and where the issue was introduced
2. Review reproduction steps and affected components (UI, API, data layer)
3. Confirm root cause category (e.g. missing validation, broken endpoint, mobile rendering issue, access control gap)
4. Document findings in the bug report
5. Suggest mitigation or prevention steps

---

### 📋 4.5 Test Case Management & Execution

Test cases managed in **Agile Test** (Jira plugin):

#### ✅ 4.5.1 General Rules

- No execution without an approved test plan
- Test cases reviewed before activation
- Each test case includes: preconditions, steps, expected result, platform tag, and traceability to feature

#### 🧾 4.5.2 Test Case Creation Rules

- Cover: happy path, negative scenarios, edge cases, boundary values
- ISTQB techniques applied explicitly: equivalence partitioning, boundary value analysis, decision table testing
- Cases grouped by module, test type, and platform
- API test cases include: endpoint, method, request body, expected status code, expected response

#### ▶️ 4.5.3 Test Case Execution

- Results logged in real time during execution
- Failed cases trigger immediate bug report creation
- Blocked cases documented with reason and rescheduled
- Postman collection results exported and attached to API test task in Jira

---

### 📊 4.6 Test Report Containment

- 📋 **Execution summary** — pass/fail counts per module, test type, and platform after each cycle
- 📈 **Defect summary** — open vs closed bugs, severity breakdown, platform distribution
- 🌐 **API summary** — endpoint coverage, failed assertions, auth validation results
- 📱 **Mobile summary** — iOS vs Android parity issues, platform-specific defects
- ♿ **Usability summary** — WCAG 2.1 AA findings, general UX observations
- 💡 **Recommendations** — risk areas identified during testing, suggestions for future coverage

---

### 📐 4.7 List of Metrics to Track

| 🧪 Metric | 🧮 Formula | ⏱️ Frequency |
|----------|-----------|-------------|
| Test Case Pass Rate | (Passed / Total Executed) × 100 | Per test cycle |
| Defect Detection Rate | Bugs found / Test cases executed | Per test cycle |
| Defect Containment Efficiency (DCE) | Bugs found before release / Total bugs | After release |
| Failed Test Cases % | (Failed / Total Executed) × 100 | Per test cycle |
| Defect Reopen Ratio | (Reopened / Total Reported) × 100 | Per test cycle |
| Requirements Coverage | (Requirements tested / Total requirements) × 100 | Per test cycle |
| API Endpoint Coverage | (Endpoints tested / Total in-scope endpoints) × 100 | Per API cycle |
| Mobile Parity Rate | (Features working on mobile / Total features tested) × 100 | Per mobile cycle |
| WCAG Issues Found | Count by level: A / AA | Per usability cycle |

---

## ⚠️ 5. Risks and Assumptions

### ⚠️ 5.1 Risks

| # | 🧨 Risk | 🔢 Probability | 🔴 Severity | 🛠️ Mitigation |
|---|---------|--------------|------------|--------------|
| 1 | OpenEMR demo environment unstable or unavailable | M | H | Schedule testing during off-peak hours; document environment issues separately |
| 2 | Demo data reset between sessions | H | M | Re-create test data at session start; keep setup steps documented |
| 3 | API endpoints undocumented or inconsistent | M | M | Use HTTP Toolkit to intercept and reverse-engineer requests; document findings |
| 4 | Mobile responsive view differs significantly from desktop | M | M | Treat mobile as a separate test layer; log parity issues explicitly |
| 5 | Physical devices unavailable for a session | L | L | Fall back to LambdaTest; reschedule physical device sessions |
| 6 | WCAG audit scope creep | L | L | Limit WCAG audit to AA level for in-scope screens only |
| 7 | Scope change mid-cycle | L | M | Lock scope at plan approval; additional modules planned for next cycle |

### 🧾 5.2 Assumptions

- OpenEMR demo environment remains accessible and functional throughout the testing period
- No real patient data is used at any point — all data is fictional
- Expected API behavior is derived from intercepted traffic and OpenEMR documentation
- Mobile testing covers the responsive web version of OpenEMR, not a native app
- WCAG 2.1 AA audit is scoped to key screens: registration, scheduling, patient search, login
- Testing is performed by a single QA Engineer acting in all roles

---

## 📱 6. Devices

| Device | OS | Usage |
|--------|----|-------|
| Physical iPhone (personal) | iOS 17+ | Manual mobile testing, usability testing |
| Physical Android device (personal) | Android 13+ | Manual mobile testing, usability testing |
| LambdaTest – cloud devices | iOS + Android (various versions) | Cross-device compatibility checks |

> Portrait orientation prioritized. Tablet testing excluded from scope.

---

## 🛠️ 7. Toolset

| Tool | Purpose |
|------|---------|
| Jira + Agile Test | Test case management, execution tracking, defect reporting |
| Confluence | Test plan and documentation storage |
| Postman | API test execution and collection management |
| HTTP Toolkit | API traffic interception and inspection |
| LambdaTest | Cross-browser and cloud mobile device testing |
| Physical iOS + Android devices | Mobile manual and usability testing |
| Miro | Test coverage mindmaps |
| GitHub | Portfolio storage and version control |

---

## 🌐 8. Test Environments

| 🏷️ Environment | 💬 Details |
|---------------|-----------|
| Demo – Web | [openemr.net/demo](https://www.openemr.net/demo) — Chrome (latest), Firefox (latest), Windows 11 |
| Demo – Mobile Web | Same demo URL via physical iOS + Android devices and LambdaTest cloud |
| API | OpenEMR REST API endpoints via demo instance; traffic intercepted via HTTP Toolkit |

---

## 📣 9. Communication Plan

| Channel | Purpose |
|---------|---------|
| Jira | Bug reports, test task tracking, execution status |
| Agile Test | Test case repository, execution results |
| Confluence | Test plan, documentation, test reports |
| Email (simulated) | Release coordination, test summary delivery |
| Slack / MS Teams (simulated) | Daily stand-up, progress updates |

---

## 🚨 10. Escalation Plan

| Situation | Action |
|-----------|--------|
| Critical bug found close to release | Immediate escalation to Product Owner; release blocked until resolved |
| Environment unavailable for 24h+ | Testing paused; rescheduled with documented justification |
| API endpoints return unexpected behavior consistently | Escalate to dev team; API testing paused pending clarification |
| Mobile parity issues affect critical workflows | Escalate to Product Owner; platform-specific fix prioritized |
| Scope change requested mid-cycle | Formal review with Product Owner; test plan updated if accepted |

---

## 🗓️ 11. Test Schedule

### 11.1 Sprint Schedule (10-day cycle)

<table>
  <thead>
    <tr>
      <th>Activity</th>
      <th>Day 1</th>
      <th>Day 2</th>
      <th>Day 3</th>
      <th>Day 4</th>
      <th>Day 5</th>
      <th>Day 6</th>
      <th>Day 7</th>
      <th>Day 8</th>
      <th>Day 9</th>
      <th>Day 10</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><strong>Test Plan & Case Design</strong></td>
      <td style="background-color:#a5d8ff">✓</td>
      <td style="background-color:#a5d8ff">✓</td>
      <td style="background-color:#a5d8ff">✓</td>
      <td></td><td></td><td></td><td></td><td></td><td></td><td></td>
    </tr>
    <tr>
      <td><strong>Manual Testing – Web</strong></td>
      <td></td><td></td>
      <td style="background-color:#8ce99a">✓</td>
      <td style="background-color:#8ce99a">✓</td>
      <td style="background-color:#8ce99a">✓</td>
      <td style="background-color:#8ce99a">✓</td>
      <td></td><td></td><td></td><td></td>
    </tr>
    <tr>
      <td><strong>Manual Testing – Mobile</strong></td>
      <td></td><td></td><td></td>
      <td style="background-color:#d3f9d8">✓</td>
      <td style="background-color:#d3f9d8">✓</td>
      <td style="background-color:#d3f9d8">✓</td>
      <td style="background-color:#d3f9d8">✓</td>
      <td></td><td></td><td></td>
    </tr>
    <tr>
      <td><strong>API Testing</strong></td>
      <td></td><td></td><td></td><td></td>
      <td style="background-color:#e0f2ff">✓</td>
      <td style="background-color:#e0f2ff">✓</td>
      <td style="background-color:#e0f2ff">✓</td>
      <td></td><td></td><td></td>
    </tr>
    <tr>
      <td><strong>Usability Testing</strong></td>
      <td></td><td></td><td></td><td></td><td></td>
      <td style="background-color:#fff3bf">✓</td>
      <td style="background-color:#fff3bf">✓</td>
      <td style="background-color:#fff3bf">✓</td>
      <td></td><td></td>
    </tr>
    <tr>
      <td><strong>Defect Retest</strong></td>
      <td></td><td></td><td></td><td></td><td></td><td></td>
      <td style="background-color:#ffc9c9">✓</td>
      <td style="background-color:#ffc9c9">✓</td>
      <td></td><td></td>
    </tr>
    <tr>
      <td><strong>Regression Testing</strong></td>
      <td></td><td></td><td></td><td></td><td></td><td></td><td></td>
      <td style="background-color:#b197fc">✓</td>
      <td style="background-color:#b197fc">✓</td>
      <td></td>
    </tr>
    <tr>
      <td><strong>Test Report & Exit</strong></td>
      <td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td>
      <td style="background-color:#ffd43b">✓</td>
      <td style="background-color:#ffd43b">✓</td>
    </tr>
  </tbody>
</table>

### 11.2 Phase Schedule

<table>
  <thead>
    <tr>
      <th style="background-color:#1d4ed8;color:white">Activity</th>
      <th style="background-color:#1d4ed8;color:white">Phase 1</th>
      <th style="background-color:#1d4ed8;color:white">Phase 2</th>
      <th style="background-color:#1d4ed8;color:white">Phase 3</th>
      <th style="background-color:#1d4ed8;color:white">Phase 4</th>
      <th style="background-color:#1d4ed8;color:white">Phase 5</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><strong>Test Planning & Case Design</strong></td>
      <td style="background-color:#a5d8ff">✓</td>
      <td></td><td></td><td></td><td></td>
    </tr>
    <tr>
      <td><strong>Manual Testing – Web</strong></td>
      <td style="background-color:#8ce99a">✓</td>
      <td style="background-color:#8ce99a">✓</td>
      <td></td><td></td><td></td>
    </tr>
    <tr>
      <td><strong>Manual Testing – Mobile</strong></td>
      <td></td>
      <td style="background-color:#d3f9d8">✓</td>
      <td style="background-color:#d3f9d8">✓</td>
      <td></td><td></td>
    </tr>
    <tr>
      <td><strong>API Testing</strong></td>
      <td></td>
      <td style="background-color:#e0f2ff">✓</td>
      <td style="background-color:#e0f2ff">✓</td>
      <td></td><td></td>
    </tr>
    <tr>
      <td><strong>Usability Testing</strong></td>
      <td></td><td></td>
      <td style="background-color:#fff3bf">✓</td>
      <td style="background-color:#fff3bf">✓</td>
      <td></td>
    </tr>
    <tr>
      <td><strong>Defect Retest</strong></td>
      <td></td><td></td>
      <td style="background-color:#ffc9c9">✓</td>
      <td style="background-color:#ffc9c9">✓</td>
      <td></td>
    </tr>
    <tr>
      <td><strong>Regression Testing</strong></td>
      <td></td><td></td><td></td>
      <td style="background-color:#b197fc">✓</td>
      <td style="background-color:#b197fc">✓</td>
    </tr>
    <tr>
      <td><strong>Test Report & Exit</strong></td>
      <td></td><td></td><td></td><td></td>
      <td style="background-color:#ffd43b">✓</td>
    </tr>
  </tbody>
</table>

---

## 🧾 12. Test Deliverables

| # | Artifact | Target Audience | Author | Frequency | Delivery Method |
|---|----------|----------------|--------|-----------|----------------|
| 1 | Test Plan | Stakeholders, Dev Team | Adrianna Golak | Once before testing; updated on scope change | Confluence / GitHub |
| 2 | Test Cases – Web | Dev Team, QA | Adrianna Golak | Before execution start | Agile Test in Jira |
| 3 | Test Cases – Mobile | Dev Team, QA | Adrianna Golak | Before execution start | Agile Test in Jira |
| 4 | Postman Collection | Dev Team, QA | Adrianna Golak | Before API cycle | Shared via Jira / Postman export |
| 5 | Bug Reports | Dev Team, Product Owner | Adrianna Golak | Upon finding a defect | Jira ticket |
| 6 | Usability Report (incl. WCAG 2.1 AA audit) | Product Owner, UX | Adrianna Golak | After usability cycle | Confluence / GitHub |
| 7 | Test Execution Report | Stakeholders | Adrianna Golak | After each test cycle | Confluence / email |
| 8 | Regression Pack | Dev Team, QA | Adrianna Golak | Per regression cycle | Agile Test in Jira |
| 9 | Test Summary Report | Product Owner, Stakeholders | Adrianna Golak | At exit | Confluence / GitHub |

---