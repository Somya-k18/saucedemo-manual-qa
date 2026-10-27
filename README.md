# SauceDemo Manual QA Testing Project

## 1. Project Overview

This repository documents a manual QA testing project performed on the public SauceDemo web application.

The project focuses on validating e-commerce workflows, identifying defects, documenting unexpected behavior, and evaluating application behavior across different browsers and viewport sizes.

It demonstrates practical QA activities, including test planning, test case design, test execution, exploratory testing, responsive compatibility testing, defect reporting, and evidence collection.

## 2. Project Objectives

- Validate core application functionality.
- Verify positive and negative user flows.
- Test application behavior across multiple browsers.
- Explore application behavior beyond predefined test cases.
- Evaluate responsive layouts at desktop, tablet, and mobile viewport sizes.
- Identify, reproduce, and document defects.
- Maintain traceability between test scenarios, execution results, defects, and evidence.

## 3. Application Under Test

| Attribute | Details |
|---|---|
| Application | SauceDemo |
| Application type | Web application |
| Testing approach | Manual testing |
| Operating system | Windows |
| Primary browser | Google Chrome |
| Additional browsers | Microsoft Edge, Mozilla Firefox |

## 4. Testing Phases

### Phase 1 — Functional Testing

Validated the application's primary workflows using 39 test cases.

Coverage included:
- Authentication and login validation
- Product catalog and sorting
- Shopping cart operations
- Checkout and order completion
- Navigation and session behavior
- Dynamic Catalog functionality

**Execution summary**

| Result | Count |
|---|---:|
| Passed | 36 |
| Failed | 3 |
| Blocked | 0 |
| Not executed | 0 |
| Total | 39 |

Execution was performed in Google Chrome.

### Phase 2 — Cross-Browser Testing

Executed 11 selected scenarios across Google Chrome, Microsoft Edge, and Mozilla Firefox, for a total of 33 browser-level executions.

The testing examined application behavior across browsers, including authentication, product interactions, cart behavior, navigation, Reset App State, and Dynamic Catalog behavior.

**Execution summary**

| Result | Count |
|---|---:|
| Passed | 27 |
| Failed | 6 |
| Total | 33 |

Nine scenarios passed in all three browsers, while two scenarios failed in all three browsers.

### Phase 3 — Exploratory Testing

Performed an exploratory session focused on application state, navigation, and transaction consistency.

The session included seven exploratory checks and investigated behavior beyond the predefined functional test cases.

A confirmed finding was that checkout accepted whitespace-only values in required customer information fields, allowing order completion and receipt generation with blank-looking customer information.

### Phase 4 — Responsive Compatibility Testing

Executed 12 scenarios across three viewport sizes, resulting in 36 viewport-level executions.

| Viewport | Dimensions |
|---|---|
| Desktop | 1366 × 768 |
| Tablet | 768 × 1024 |
| Mobile | 390 × 844 |

Testing focused on layout behavior, visibility of interface elements, validation messages, product cards, and Dynamic Catalog presentation.

The testing identified issues involving clipped content, excessive spacing, and image display, alongside observations requiring further investigation.

## 5. Defects Identified

Seven defects were documented during the project.

| Defect ID | Area | Summary | Severity |
|---|---|---|---|
| BUG-001 | Navigation & Session | Session expiration displays page-specific authentication errors | Medium |
| BUG-002 | Dynamic Catalog | Duplicate products are generated while scrolling | Medium |
| BUG-003 | Navigation & Session | Reset App State leaves stale interface state | Medium |
| BUG-004 | Checkout | Whitespace-only required fields are accepted | High |
| BUG-005 | Dynamic Catalog | Images are clipped within displayed areas | Medium |
| BUG-006 | Authentication | Invalid-credentials error message is partially clipped | Medium (provisional) |
| BUG-007 | Products | Excessive vertical spacing in mobile product cards | Medium (provisional) |

Severity and priority are documented in the individual defect reports. Provisional classifications remain subject to review against the project's impact criteria.

## 6. Repository Contents

The repository contains the following project artifacts:

- **Test Plan** — testing objectives, scope, approach, environments, and coverage.
- **Manual Test Cases** — predefined functional test cases and their execution details.
- **Test Execution Report** — execution summaries and findings across the testing phases.
- **Cross-Browser Test Matrix** — browser-specific test results.
- **Responsive Compatibility Test Matrix** — viewport-specific test results.
- **Defect Reports** — reproducible descriptions of identified defects.
- **Evidence** — screenshots supporting defect reports and test observations.

See the repository folders for the corresponding files and supporting evidence.

## 7. Test Environment

### Browsers

- Google Chrome 155.0.8059.40 (64-bit)
- Microsoft Edge 154.0.4258.62 (64-bit)
- Mozilla Firefox 157.0.1 (64-bit)

### Platform

- Operating system: Windows
- Testing method: Manual
- Application: Public SauceDemo web application

Browser versions and viewport dimensions reflect the recorded test environment.

## 8. Defect Reporting Approach

Defects were documented using a structured format that includes, where applicable:

- Defect ID and title
- Module and category
- Severity and priority
- Environment and preconditions
- Steps to reproduce
- Expected result
- Actual result
- Evidence
- Relationship to other defects
- Notes and limitations

Findings were evaluated based on observable behavior. Unexpected behavior was not automatically classified as a defect when the expected behavior could not be established.

## 9. Testing Limitations

This project represents a focused manual QA exercise. The following areas were outside its defined scope:

- Performance and load testing
- Security penetration testing
- Backend and API testing
- Database testing
- Accessibility compliance testing
- Mobile application testing
- Source-code review

The project evaluates the observable behavior of the public application and does not establish underlying technical causes for reported defects.

## 10. Project Status

The project documents four testing phases:

1. Functional testing
2. Cross-browser testing
3. Exploratory testing
4. Responsive compatibility testing

Test cases, execution results, defect reports, and supporting evidence form the project's QA documentation.

## 11. Purpose of the Project

This project serves as a practical demonstration of manual QA skills, including test design, test execution, cross-browser validation, responsive testing, defect documentation, and evidence-based reporting.

The findings and results are limited to the recorded test environment, scenarios, and observations.