# SauceDemo Manual QA — Test Plan

## 1. Project Overview

This project demonstrates a structured manual QA testing process performed on the public SauceDemo web application.

Testing covers authentication, product catalog, shopping cart, checkout, navigation and session behavior, application state reset, Dynamic Catalog functionality, cross-browser compatibility, exploratory testing, and responsive web behavior across selected desktop, tablet, and mobile viewport sizes.

The project demonstrates:

- Test planning
- Manual test case design
- Test execution
- Exploratory testing
- Cross-browser compatibility testing
- Responsive compatibility testing
- Defect identification and classification
- Evidence collection
- Professional defect reporting
- Test result documentation
- Regression testing

## 2. Application Under Test

**Application:** SauceDemo  
**Application Type:** Web application  
**Testing Type:** Manual Testing

The application provides an e-commerce-style workflow including user authentication, product browsing, cart management, checkout, application state reset, and order completion.

## 3. Testing Objectives

The objectives of this testing activity are to:

1. Verify that users can log in using valid and invalid credentials.
2. Verify core product catalog functionality.
3. Verify shopping cart operations.
4. Verify checkout and order completion workflows.
5. Verify navigation and session-related behavior.
6. Verify the Reset App State functionality.
7. Explore the Dynamic Catalog functionality.
8. Verify selected workflows across supported desktop browsers.
9. Evaluate layout and usability across selected viewport sizes.
10. Identify unexpected behaviors and determine whether they represent defects.
11. Document confirmed defects with reproducible steps and evidence.
12. Perform regression testing of relevant functionality where required.

## 4. Scope

### In Scope

- User login and authentication
- Login validation and error messages
- Product catalog
- Product details
- Product sorting
- Add to Cart and Remove operations
- Shopping cart
- Checkout information validation
- Order overview
- Order completion
- PDF order receipt generation
- Application navigation
- Browser Back navigation
- Session-related behavior
- Reset App State functionality
- Dynamic Catalog sections
- Exploratory testing
- Cross-browser compatibility testing
- Responsive web behavior at selected viewport sizes
- Regression testing of relevant functionality

### Out of Scope

- Performance and load testing
- Security penetration testing
- Source-code review
- Backend/API testing
- Database testing
- Native mobile application testing
- Full accessibility compliance certification

## 5. Test Environment

### Primary Environment

**Application:** SauceDemo web application  
**Test Type:** Manual  
**Platform:** Windows

### Browser Coverage

Cross-browser testing was performed using the following desktop browsers:

| Browser | Version | Platform |
|---|---|---|
| Google Chrome | 155.0.8059.40 (64-bit) | Windows 64-bit |
| Microsoft Edge | 154.0.4258.62 (64-bit) | Windows 64-bit |
| Mozilla Firefox | 157.0.1 (64-bit) | Windows 64-bit |

### Responsive Compatibility Coverage

Responsive web behavior was evaluated at the following viewport sizes:

| Viewport Category | Viewport Size |
|---|---|
| Desktop | 1366 × 768 |
| Tablet | 768 × 1024 |
| Mobile | 390 × 844 |

Testing was performed against the publicly accessible application during October 2026.

## 6. Test Approach

Testing was performed using a combination of the following approaches.

### Functional Testing

Predefined test cases were executed to verify expected application behavior across the major functional areas.

### Positive Testing

Valid inputs and expected user flows were tested to confirm successful operations.

### Negative Testing

Invalid, missing, and boundary-related inputs were tested where applicable to verify validation and error handling.

### Exploratory Testing

Exploratory testing was performed in addition to formal test-case execution to identify unexpected behavior and areas requiring further investigation.

Findings were evaluated against observable application behavior before being classified as defects.

### Cross-Browser Testing

Selected workflows were tested across Google Chrome, Microsoft Edge, and Mozilla Firefox to identify browser-specific functional, layout, navigation, or usability issues.

Cross-browser testing focused on selected workflows rather than duplicating every functional test case across all browsers.

### Responsive Compatibility Testing

Selected application workflows were evaluated at desktop, tablet, and mobile viewport sizes to identify layout, visibility, clipping, spacing, and usability issues.

This testing covered the responsive web application and did not include native mobile applications.

### Regression Testing

Relevant test cases were re-executed after defect investigation or application-state changes to determine whether previously observed behavior persisted and whether related functionality remained unaffected.

## 7. Test Data

The following SauceDemo-provided test accounts were used where applicable:

- `standard_user`
- `locked_out_user`

For checkout testing, valid, invalid, missing, and whitespace-only combinations of the following fields were used:

- First Name
- Last Name
- Postal Code

## 8. Test Coverage

The testing activity was divided into four phases.

### Phase 1 — Functional Testing

The formal functional test suite contains **39 test cases** across six functional areas.

| Module | Test Cases |
|---|---:|
| Authentication | 7 |
| Products | 8 |
| Cart | 7 |
| Checkout | 7 |
| Navigation & Session | 6 |
| Dynamic Catalog | 4 |
| **Total** | **39** |

The Phase 1 execution results were:

| Result | Test Cases |
|---|---:|
| Passed | 36 |
| Failed | 3 |
| Blocked | 0 |
| Not Executed | 0 |
| **Total** | **39** |

**Pass rate:** 92.3%

The three failed test cases were associated with BUG-001, BUG-002, and BUG-003.

### Phase 2 — Cross-Browser Testing

Cross-browser testing covered 11 selected workflows across Google Chrome, Microsoft Edge, and Mozilla Firefox.

#### Test Environment

| Browser | Version | Platform |
|---|---|---|
| Chrome | 155.0.8059.40 (64-bit) | Windows 64-bit |
| Edge | 154.0.4258.62 (64-bit) | Windows 64-bit |
| Firefox | 157.0.1 (64-bit) | Windows 64-bit |

#### Test Coverage

| Metric | Count |
|---|---:|
| Selected cross-browser test scenarios | 11 |
| Browsers tested | 3 |
| Total browser-level executions | 33 |

#### Execution Summary

| Result | Scenarios |
|---|---:|
| Passed in all three browsers | 9 |
| Failed in all three browsers | 2 |
| Blocked | 0 |
| Not Executed | 0 |
| **Total** | **11** |

Nine scenarios passed across all three browsers. Two scenarios failed across all three browsers.

The following existing defects were reproduced:

- **BUG-002:** Dynamic Catalog generates duplicate products while scrolling.
- **BUG-003:** Reset App State leaves the product button in a stale `Remove` state.

Other browser-specific and cart-related behaviors were recorded as observations where the available evidence did not establish a confirmed defect.

### Phase 3 — Exploratory Testing

One exploratory session was completed using the charter **ET-SESSION-01 — State, Navigation and Transaction Consistency**.

Seven exploratory checks covered cart state, navigation, checkout form validation, order summary accuracy, and transaction consistency.

| Metric | Result |
|---|---|
| Completed exploratory sessions | 1 |
| Completed exploratory checks | 7 |
| Confirmed defect identified | BUG-004 |
| Additional unconfirmed observations | 1 |

**BUG-004** concerns the acceptance of whitespace-only required checkout fields.

Inconsistent Browser Back/Forward behavior was also observed. It was not classified as a confirmed defect because it could not be reproduced consistently.

Detailed findings are documented in `Test-Execution/Exploratory-Test-Session-Report.md`.

### Phase 4 — Compatibility / Responsive Testing

Responsive testing covered 12 scenarios at three viewport sizes: desktop, tablet, and mobile.

| Viewport Category | Viewport Size | Scenarios |
|---|---|---:|
| Desktop | 1366 × 768 | 12 |
| Tablet | 768 × 1024 | 12 |
| Mobile | 390 × 844 | 12 |
| **Total** | | **36 viewport-level executions** |

The responsive compatibility matrix is maintained in `Test-Cases/Responsive-Compatibility-Test-Matrix.xlsx`.

#### Key Findings

- **RC-001:** The mobile login page's accepted-user information extends below the initially visible viewport. Further investigation is needed to determine whether all information is accessible through normal scrolling.
- **RC-002:** The invalid-credentials error message is partially clipped and not fully readable within the red error container on desktop and mobile viewports. The issue was not observed on the tablet viewport during testing. This is tracked as **BUG-006**.
- **RC-003:** Excessive vertical spacing in mobile product cards pushes the price and Add to Cart controls farther down the page, requiring users to scroll to reach them. Desktop and tablet layouts did not exhibit this issue during testing. This is tracked as **BUG-007**.
- **RC-004:** Product sorting resets after returning from the cart. This remains an observation pending confirmation of the expected behavior.
- **RC-007:** Whitespace-only required checkout values are accepted, reproducing **BUG-004**.
- **RC-011:** Reset App State leaves stale product button state and, under the recorded conditions, stale cart contents visible. This reproduces **BUG-003**.
- **RC-012:** Dynamic Catalog generates duplicate products while scrolling and displays clipped images. These findings reproduce **BUG-002** and **BUG-005**.

RC-002 and RC-003 are recorded as defects based on the observed and documented behavior. RC-001 and RC-004 remain observations pending further investigation or confirmation of expected behavior.

### Overall Coverage

| Phase | Coverage | Status |
|---|---|---|
| Phase 1 — Functional | 39 formal test cases | Completed |
| Phase 2 — Cross-Browser | 11 scenarios across 3 browsers; 33 browser-level executions | Completed |
| Phase 3 — Exploratory | 1 charter; 7 exploratory checks | Completed |
| Phase 4 — Compatibility / Responsive | 12 scenarios across 3 viewport sizes; 36 viewport-level executions | Completed |

The phase totals use different measurement units and should not be added together as a single test-case count. Regression testing uses relevant existing test cases and additional scenarios where required.

## 9. Entry Criteria

Testing could begin when:

- The application was accessible.
- A supported browser was available.
- Valid SauceDemo test credentials were available.
- Test cases had been prepared.
- Required test data was available.
- Required browser environments were available for compatibility testing.

## 10. Exit Criteria

Testing is considered complete when:

- All planned test cases have been executed.
- Planned cross-browser coverage has been completed.
- Planned responsive compatibility scenarios have been executed.
- Relevant exploratory testing has been performed.
- Failed test cases have been investigated.
- Confirmed defects have been documented.
- Supporting evidence has been collected where applicable.
- Relevant regression testing has been completed.
- Test execution results have been recorded.

## 11. Defect Classification

Defects were evaluated based on:

- Reproducibility
- Impact on user experience or functionality
- Expected versus actual behavior
- Severity
- Priority
- Affected browser or viewport, where applicable

An unexpected observation was not automatically classified as a defect when the expected behavior could not be established from the available application behavior.

### Severity Criteria

Severity represents the impact of a defect on application functionality and user experience.

| Severity | Definition |
|---|---|
| Critical | A critical application workflow is unusable, with no reasonable workaround. |
| High | A major function is broken or an important workflow is significantly impaired. |
| Medium | Functionality works incorrectly or has a noticeable usability or validation issue, but the overall application remains usable. |
| Low | A minor visual or usability issue has limited impact on functionality. |

### Priority Criteria

Priority represents the urgency with which a defect should be addressed.

| Priority | Definition |
|---|---|
| High | Requires prompt correction because of substantial user impact or risk to a critical workflow. |
| Medium | Should be addressed in a planned development or maintenance cycle. |
| Low | Can be scheduled later because the impact is limited. |

These criteria are defined for this portfolio project. Severity and priority assignments are based on observed behavior, affected functionality, user impact, and available evidence. They do not represent an official classification scheme from the application owner.

## 12. Deliverables

The project includes:

- Test Plan
- Manual Test Cases
- Test Execution Report
- Cross-Browser Test Matrix
- Responsive Compatibility Test Matrix
- Exploratory Test Session Report
- Defect Reports
- Defect Evidence
- Project README

## 13. Testing Limitations

This project represents a structured manual testing exercise rather than a complete production QA cycle.

The following limitations apply:

- Testing was performed on a public application without access to business requirements or source code.
- Cross-browser coverage is limited to the browsers and versions documented in the test records.
- Responsive testing is limited to desktop (1366 × 768), tablet (768 × 1024), and mobile (390 × 844) viewport sizes. It does not establish full device or browser compatibility.
- Performance and security testing were not performed.
- Native mobile application testing was not performed.
- Some behaviors could only be classified as observations where an explicit expected behavior was not available.
- Session expiration timing was observed approximately rather than measured as an exact timeout value.
- RC-001 and RC-004 remain observations pending further investigation or confirmation of expected behavior.

## 14. Defects Identified

**Seven defects are documented** across functional, cross-browser, exploratory, and responsive compatibility testing.

| Defect ID | Area | Summary | Severity | Priority |
|---|---|---|---|---|
| BUG-001 | Navigation & Session | Session expiration displays raw, page-specific authentication errors instead of graceful session handling. | Medium | Medium |
| BUG-002 | Dynamic Catalog | Dynamic Catalog continuously generates duplicate products while scrolling. | Medium | Medium |
| BUG-003 | Navigation & Session | Reset App State leaves stale cart contents and product button state visible under the recorded conditions. | Medium | Medium |
| BUG-004 | Checkout | Checkout accepts whitespace-only required fields, allowing order completion and receipt generation with blank-looking customer information. | High | Medium (Provisional) |
| BUG-005 | Dynamic Catalog | Dynamic Catalog images are clipped in Lazy Load, Spinner, and Slider sections. | Medium | Medium |
| BUG-006 | Login Validation / Responsive UI | Invalid-credentials error message is partially clipped on desktop and mobile viewports. | Medium | Medium |
| BUG-007 | Product Catalog / Responsive UI | Excessive vertical spacing in mobile product cards pushes price and Add to Cart controls farther down the page. | Medium | Medium |

Severity and priority should be treated as project-level assessments and revised if further evidence changes the estimated impact or urgency.

## 15. Traceability

Each formal test case contains a unique Test Case ID.

Failed test cases are linked to their corresponding defect IDs in the test case and execution documentation.

Cross-browser and responsive compatibility findings are linked to the relevant test scenario, browser or viewport environment, result, defect ID, and supporting evidence where applicable.

The responsive results are maintained in `Test-Cases/Responsive-Compatibility-Test-Matrix.xlsx`.

This provides traceability from:

**Test Case → Execution Result → Defect → Evidence**

Where applicable, cross-browser and responsive testing also provides traceability from:

**Test Scenario → Browser/Viewport → Result → Defect → Evidence**