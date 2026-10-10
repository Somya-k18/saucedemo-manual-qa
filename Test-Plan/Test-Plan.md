# SauceDemo Manual QA — Test Plan

## 1. Project Overview

This project demonstrates a structured manual QA testing process performed on the public SauceDemo web application.

The testing covers functional testing of authentication, product catalog, shopping cart, checkout, navigation/session behavior, application state reset, Dynamic Catalog functionality, and cross-browser compatibility.

The project demonstrates:

* Test planning
* Manual test case design
* Test execution
* Exploratory testing
* Cross-browser compatibility testing
* Defect identification and classification
* Evidence collection
* Professional defect reporting
* Test result documentation
* Regression testing

## 2. Application Under Test

**Application:** SauceDemo
**Application Type:** Web application
**Testing Type:** Manual Testing

The application provides an e-commerce-style workflow including user authentication, product browsing, cart management, checkout, application state reset, and order completion.

## 3. Testing Objectives

The objectives of this testing activity are to:

1. Verify that users can successfully log in using valid and invalid credentials.
2. Verify core product catalog functionality.
3. Verify shopping cart operations.
4. Verify checkout and order completion workflows.
5. Verify navigation and session-related behavior.
6. Verify the Reset App State functionality.
7. Explore the Dynamic Catalog functionality.
8. Verify critical application workflows across supported desktop browsers.
9. Identify unexpected behaviors and determine whether they represent defects.
10. Document confirmed defects with reproducible steps and evidence.
11. Perform regression testing of relevant functionality where required.

## 4. Scope

### In Scope

* User login and authentication
* Login validation and error messages
* Product catalog
* Product details
* Product sorting
* Add to Cart / Remove operations
* Shopping cart
* Checkout information validation
* Order overview
* Order completion
* PDF order receipt generation
* Application navigation
* Browser Back navigation
* Session-related behavior
* Reset App State functionality
* Dynamic Catalog sections
* Exploratory testing
* Cross-browser compatibility testing
* Responsive web behavior at selected viewport sizes
* Regression testing of relevant functionality

### Out of Scope

* Performance/load testing
* Security penetration testing
* Source-code review
* Backend/API testing
* Database testing
* Native mobile application testing
* Full accessibility compliance certification

## 5. Test Environment

### Primary Environment

**Application:** SauceDemo web application
**Test Type:** Manual
**Platform:** Windows

### Browser Coverage

Cross-browser testing will be performed using supported desktop browsers, including:

* Google Chrome
* Microsoft Edge
* Mozilla Firefox

Actual browser versions and test results will be recorded during test execution.

### Additional Compatibility Coverage

Selected workflows will also be evaluated at different browser viewport sizes to identify obvious responsive-layout or usability issues.

Testing was performed against the publicly accessible application during October 2026.

## 6. Test Approach

Testing is performed using a combination of:

### Functional Testing

Predefined test cases are executed to verify expected application behavior across the major functional areas.

### Positive Testing

Valid inputs and expected user flows are tested to confirm successful operations.

### Negative Testing

Invalid, missing, and boundary-related inputs are tested where applicable to verify validation and error handling.

### Exploratory Testing

Exploratory testing is performed in addition to formal test-case execution to identify unexpected behaviors and areas requiring further investigation.

Findings are evaluated against observable application behavior before being classified as defects.

### Cross-Browser Testing

Selected critical workflows are tested across supported desktop browsers to identify browser-specific functional, layout, navigation, or usability issues.

Cross-browser testing is focused on meaningful user workflows rather than duplicating every test case across every browser.

### Regression Testing

Relevant test cases are re-executed after defect investigation or application-state changes to determine whether previously observed behavior persists and whether related functionality remains unaffected.

## 7. Test Data

The following SauceDemo-provided test accounts are used where applicable:

* `standard_user`
* `locked_out_user`

For checkout testing, valid and invalid combinations of:

* First Name
* Last Name
* Postal Code

are used.

## 8. Test Coverage

The test strategy is divided into four testing phases. The formal functional suite currently contains **39 test cases**. Additional test cases, matrices, and exploratory charters will be created and executed as the subsequent testing phases are performed.

### Phase 1 — Functional Testing

The current formal functional test suite contains **39 test cases** across six functional areas.

| Module               | Test Cases |
| -------------------- | ---------: |
| Authentication       |          7 |
| Products             |          8 |
| Cart                 |          7 |
| Checkout             |          7 |
| Navigation & Session |          6 |
| Dynamic Catalog      |          4 |
| **Phase 1 Total**    |     **39** |

### Phase 2 — Cross-Browser Testing

Cross-browser testing verified 11 selected workflows across Google Chrome, Microsoft Edge, and Mozilla Firefox. The suite focused on compatibility of selected workflows rather than duplicating all 39 functional test cases across every browser.


**Test Environment**

| Browser | Version | Platform |
|---|---|---|
| Chrome | 155.0.8059.40 (64-bit) | Windows 64-bit |
| Edge | 154.0.4258.62 (64-bit) | Windows 64-bit |
| Firefox | 157.0.1 (64-bit) | Windows 64-bit |


**Test Coverage**

| Metric | Count |
|---|---:|
| Selected cross-browser test cases | 11 |
| Browsers tested | 3 |
| Total browser-level executions | 33 |


**Execution Status**

| Result | Test Cases |
|---|---:|
| Passed | 9 |
| Failed | 2 |
| Blocked | 0 |
| Not Executed | 0 |
| **Total** | **11** |


The results above summarize the 11 test scenarios overall; each scenario was executed in all three browsers.

Two existing defects were reproduced across all three browsers: BUG-002 (duplicate products during Dynamic Catalog scrolling) and BUG-003 (stale product button state after Reset App State). Additional browser-specific and cart observations were documented without classifying them as confirmed defects.

### Phase 3 — Exploratory Testing

Exploratory testing will use structured exploratory charters covering areas such as navigation, application state, session behavior, repeated actions, refresh/back/forward behavior, and Dynamic Catalog behavior.

| Exploratory Area                           | Test Charters |
| ------------------------------------------ | ------------: |
| Navigation & Session                       |           TBD |
| Application State                          |           TBD |
| User Interaction / Repeated Actions        |           TBD |
| Dynamic Catalog                            |           TBD |
| Additional Areas Identified During Testing |           TBD |
| **Phase 3 Total**                          |       **TBD** |

### Phase 4 — Compatibility / Responsive Testing

Responsive testing will evaluate the web application at selected viewport sizes and document layout, usability, visibility, and interaction issues.

| Viewport Category | Test Cases |
| ----------------- | ---------: |
| Desktop           |        TBD |
| Tablet            |        TBD |
| Mobile            |        TBD |
| **Phase 4 Total** |    **TBD** |

### Overall Coverage

| Phase                                | Planned Coverage |
| ------------------------------------ | ---------------: |
| Phase 1 — Functional                 |               39 |
| Phase 2 — Cross-Browser              |              TBD |
| Phase 3 — Exploratory                |              TBD |
| Phase 4 — Compatibility / Responsive |              TBD |
| **Overall Total**                    |          **TBD** |

The Phase 2–4 counts will be finalized after the corresponding test cases, matrices, and exploratory charters are designed. Regression testing will use relevant existing test cases and newly identified scenarios rather than being treated as a separate duplicate test suite.

## 9. Entry Criteria

Testing can begin when:

* The application is accessible.
* A supported browser is available.
* Valid SauceDemo test credentials are available.
* Test cases have been prepared.
* Required test data is available.
* The required browser environments are available for compatibility testing.

## 10. Exit Criteria

Testing is considered complete when:

* All planned test cases have been executed.
* Planned cross-browser coverage has been completed.
* Relevant exploratory testing has been performed.
* Failed test cases have been investigated.
* Confirmed defects have been documented.
* Supporting evidence has been collected where applicable.
* Relevant regression testing has been completed.
* Test execution results have been recorded.

## 11. Defect Classification

Defects are evaluated based on:

* Reproducibility
* Impact on user experience or functionality
* Expected versus actual behavior
* Severity
* Priority
* Affected browser or environment, where applicable

An unexpected observation is not automatically classified as a defect when the expected behavior cannot be established from the available application behavior.

## 12. Deliverables

The project includes:

* Test Plan
* Manual Test Cases
* Test Execution Report
* Cross-Browser Test Results
* Defect Reports
* Defect Evidence
* Project README

Additional test documentation may be added as the testing scope expands.

## 13. Testing Limitations

This project represents a structured manual testing exercise rather than a complete production QA cycle.

The following limitations apply:

* Testing is performed on a public application without access to business requirements or source code.
* Cross-browser coverage is limited to the browsers and versions documented in the Test Execution Report.
* Responsive testing is limited to selected viewport sizes.
* Performance and security testing are not performed.
* Some behaviors can only be classified as observations where an explicit expected behavior is not available.
* Session expiration timing was observed approximately rather than measured as an exact timeout value.
* Native mobile application testing is not included.

## 14. Defects Identified So Far

Three confirmed defects have been identified during the current testing cycle:

| Defect ID | Area                 | Summary                                                                                                   | Severity | Priority |
| --------- | -------------------- | --------------------------------------------------------------------------------------------------------- | -------- | -------- |
| BUG-001   | Navigation & Session | Session expiration displays raw, page-specific authentication errors instead of graceful session handling | Medium   | Medium   |
| BUG-002   | Dynamic Catalog      | Dynamic Catalog continuously generates duplicate products while scrolling                                 | Medium   | Medium   |
| BUG-003   | Navigation & Session | Reset App State clears cart data but leaves stale Remove button state until page refresh                  | Medium   | Medium   |

Additional defects may be identified during cross-browser, responsive, exploratory, or regression testing.

## 15. Traceability

Each formal test case contains a unique Test Case ID.

Failed test cases are linked to their corresponding defect IDs in the test case and execution documentation.

Cross-browser findings and additional defects will be linked to the relevant test scenario, browser/environment, and supporting evidence where applicable.

This provides traceability from:

**Test Case → Execution Result → Defect → Evidence**

and, where applicable:

**Test Scenario → Browser/Environment → Result → Defect → Evidence**
