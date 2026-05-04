# Test Plan - OpenEMR Patient Management Application

**Version:** 1.0
**Author:** Adrianna Golak
**Date:** 2025-05-03
**Status:** In Review

---

## 1. Introduction

This test plan covers the quality assurance strategy for the **Patient
Management** module of OpenEMR - an open-source Electronic Medical
Records system used worldwide in clinical environments.

The goal is to validate that the core workflows function
correctly and in line with expected business behavior.

---

## 2. Scope

### In scope
- Patient registration (new patient creation)
- Patient search and record retrieval
- Appointment scheduling
- Prescription creation and validation
- User roles and access control (admin, physician, nurse, receptionist)
- Creating and editing medical records

### Out of scope 
- Automated test execution
- Performance and load testing 
- Third-party integrations (eg. insurance systems, external labs)
- Mobile application

---

## 3. Test objectives

- Verify that patient data is created and saved correctly
- Confirm that role-based access control doesn't allow unauthorized actions
- Validate appointment and prescription workflows
- Validate form field behavior (required fields, input limits, error messages)

---

## 4. Test strategy

### Approach
Risk-based testing - priority given to workflows with the highest impact
on patient safety and data integrity.

### Test types
| Type | Description |
| --- | --- |
| Functional testing | Verify features work as specified |
| Negative testing | Validate system behavior for invalid inputs |
| Boundary value analysis | Test field limits and edge cases |
| Role-based testing | Confirm access control per user type |
| Regression testing | Ensure new changes don't break existing features |

### Test design techniques
- Equivalence partitioning
- Boundary value analysis
- Decision table testing (for role permissions)
- Use case-based testing

---

## 5. Risk assessment

| Risk | Likelihood | Impact | Mitigation |
| --- | --- | --- | --- |
| Incorrect patient data saved | Medium | High | Cover all registration fields in test cases |
| Unauthorized access to records | Low | Critical | Dedicated role-based test suite |
| Appointment conflicts not flagged | Medium | High | Test scheduling edge cases explicitly |
| Data saved without required fields | Low | Critical | Negative test cases for all mandatory fields |
| Data loss on session timeout | Low | High | Test session handling separately |

---

## 6. Entry criteria

- Test environment is set up and accessible
- OpenEMR demo instance is available and stable
- Test cases are ready for execution (test execution is prepared)
- Test data (patient records, user accounts per role) is prepared

---

## 7. Exit criteria

- All planned test cases executed
- No open Critical or High severity bugs
- Test execution report completed
- Known Medium/Low issues documented

---

## 8. Test environment

| Parameter | Value |
| --- | --- |
| Application | OpenEMR (open-source EMR) |
| Environment | Demo instance - openemr.net/demo |
| Browsers | Chrome (latest), Firefox (latest), Safari (on MacOS, latest) |
| OS | Windows 11 | macOS |
| Test data | Fictional patient and user data |

---

## 9. Test deliverables

- Test Plan (this document)
- Bug Reports
- Test Execution Report with QA metrics

---

## 10. Roles and responsibilities

| Role | Responsibility |
| --- | --- |
| QA Engineer (Adrianna Golak) | Test planning, test case design, execution, reporting |

---

## 11. Schedule

| Phase | Activity |
| --- | --- |
| Phase 1 | Test planning and test case design |
| Phase 2 | Test execution |
| Phase 3 | Bug reporting and triage |
| Phase 4 | Test summary report |

---

## 12. Assumptions and constraints

- Testing is based on the publicly available OpenEMR demo environment
- No real patient data is used at any point
- Test scope limited to manual functional testing
- Environment stability depends on the OpenEMR demo availability