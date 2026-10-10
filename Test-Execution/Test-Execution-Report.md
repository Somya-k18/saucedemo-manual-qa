# SauceDemo Manual QA — Test Execution Report

## 1. Execution Overview

**Project:** SauceDemo Manual QA Testing

**Testing Phase:** Phase 1 — Functional Testing

**Report Scope:** Phase 1 functional testing and Phase 2 cross-browser testing. Phase-specific results are documented separately below.

**Application:** SauceDemo Web Application

**Test Type:** Manual Testing

**Execution Status:** Phases 1 and 2 completed; Phases 3 and 4 pending

**Total Test Cases Executed:** 39 (Phase 1 functional suite)

## 2. Test Environment

- **Operating System:** Windows
- **Application:** SauceDemo Web Application
- **Primary Browser:** Google Chrome
- **Browser Coverage:** Phase 1 functional execution performed in Chrome
- **Test Data:** SauceDemo standard and predefined user accounts, along with valid and invalid checkout data as applicable to individual test cases

## 3. Test Execution Summary

| Result | Count |
|---|---:|
| Total Test Cases | 39 |
| Passed | 36 |
| Failed | 3 |
| Blocked | 0 |
| Not Executed | 0 |
| **Phase 1 Pass Rate** | **92.3%** |

## 4. Module-wise Execution Results

| Module | Total | Passed | Failed |
|---|---:|---:|---:|
| Authentication | 7 | 7 | 0 |
| Products | 8 | 8 | 0 |
| Cart | 7 | 7 | 0 |
| Checkout | 7 | 7 | 0 |
| Navigation & Session | 6 | 4 | 2 |
| Dynamic Catalog | 4 | 3 | 1 |
| **Total** | **39** | **36** | **3** |

## 5. Failed Test Cases

### TC-NAV-005 — Prolonged Inactivity / Session Expiration

**Status:** Failed

**Defect:** BUG-001

After a period of inactivity, the session became invalid and the application displayed page-specific authentication error messages when accessing protected routes, including `/inventory.html` and `/cart.html`.

**Defect Report:** `Bug-Reports/BUG-001.md`

---

### TC-NAV-006 — Reset App State

**Status:** Failed

**Defect:** BUG-003

Reset App State successfully cleared the cart and removed the cart badge, but the product button continued to display **Remove** even though the product was no longer in the cart.

The button returned to **Add to cart** after page reload or navigation that refreshed the product state.

**Defect Report:** `Bug-Reports/BUG-003.md`

---

### TC-DYN-003 — Dynamic Catalog Duplicate Products

**Status:** Failed

**Defect:** BUG-002

The Dynamic Catalog Lazy Load section continuously generated duplicate product entries while scrolling.

**Defect Report:** `Bug-Reports/BUG-002.md`

## 6. Defects Identified

| Defect ID | Related Test Case | Module | Severity | Priority | Status |
|---|---|---|---|---|---|
| BUG-001 | TC-NAV-005 | Navigation & Session | Medium | Medium | Open |
| BUG-002 | TC-DYN-003 | Dynamic Catalog | Medium | Medium | Open |
| BUG-003 | TC-NAV-006 | Navigation & Session | Medium | Medium | Open |

## 7. Evidence

Evidence captured during Phase 1 execution is stored in the following repository directories:

- `Evidence/BUG-001/`
- `Evidence/BUG-002/`
- `Evidence/BUG-003/`

The corresponding defect reports contain the filenames and descriptions of the supporting screenshots.

## 8. Observations

During functional testing, several application behaviors were observed but were not classified as confirmed defects because the expected behavior or applicable requirement had not been established.

- **Dynamic Catalog interaction limitations:** The Spinner subsection displayed product entries without visible spinning or movement, and some Dynamic Catalog sections provided limited product details and no Add to Cart option.
- **Cart quantity-control behavior:** The cart did not provide quantity adjustment controls. The product button changed from "Add to cart" to "Remove" after selection, and the same product could not be added again while selected.
- **About-page navigation:** Selecting About redirected the user to the Sauce Labs website. Returning to the application required using the browser's Back function.
- **Checkout with an empty cart:** The application allowed checkout to proceed and an order to be completed with no products in the cart, resulting in a total of $0.00.

These findings were documented as observations rather than confirmed defects because sufficient evidence of a requirement violation had not been established. Confirmed defects are documented separately in Section 6 and the corresponding defect reports.

## 9. Phase 1 Conclusion

Phase 1 functional testing was completed with all **39 planned functional test cases executed**.

A total of **36 test cases passed** and **3 failed**, resulting in a **92.3% pass rate** for the executed functional suite.

Three reproducible defects were documented with supporting evidence:

- **BUG-001** — Session expiration error handling
- **BUG-002** — Dynamic Catalog duplicate products
- **BUG-003** — Reset App State UI state inconsistency

Further testing remains planned as part of the broader QA strategy:

- **Phase 3 — Exploratory Testing**
- **Phase 4 — Compatibility / Responsive Testing**

The results in this section represent **Phase 1 functional testing only**. Cross-browser testing results are documented separately in Section 10. Final project-level conclusions will be updated after the remaining testing phases are completed.

---

## 10. Phase 2 — Cross-Browser Test Execution

### 10.1 Execution Overview

| Metric | Result |
|---|---:|
| Testing Phase | Phase 2 — Cross-Browser Testing |
| Browsers Tested | 3 |
| Cross-Browser Test Cases | 11 |
| Total Browser-Level Executions | 33 |
| Passed Test Cases | 9 |
| Failed Test Cases | 2 |
| Blocked Test Cases | 0 |
| Not Executed | 0 |

Each of the 11 selected test scenarios was executed in Chrome, Edge, and Firefox, resulting in 33 browser-level executions. Nine scenarios passed in all three browsers, while two scenarios failed in all three. Individual browser results are recorded in the cross-browser test matrix.

### 10.2 Test Environment

| Browser | Version | Platform |
|---|---|---|
| Google Chrome | 155.0.8059.40 (64-bit) | Windows 64-bit |
| Microsoft Edge | 154.0.4258.62 (64-bit) | Windows 64-bit |
| Mozilla Firefox | 157.0.1 (64-bit) | Windows 64-bit |

### 10.3 Cross-Browser Results

| CB ID | Test Scenario | Chrome | Edge | Firefox | Overall Result |
|---|---|---|---|---|---|
| CB-001 | Login with valid credentials | Pass | Pass | Pass | Pass |
| CB-002 | Product catalog loads correctly | Pass | Pass | Pass | Pass |
| CB-003 | Product details open correctly | Pass | Pass | Pass | Pass |
| CB-004 | Add product to cart | Pass | Pass | Pass | Pass |
| CB-005 | Remove product from cart | Pass | Pass | Pass | Pass |
| CB-006 | Cart displays selected product correctly | Pass | Pass | Pass | Pass |
| CB-007 | Checkout workflow | Pass | Pass | Pass | Pass |
| CB-008 | Complete an order | Pass | Pass | Pass | Pass |
| CB-009 | Reset App State | Fail | Fail | Fail | Fail |
| CB-010 | Dynamic Catalog scrolling | Fail | Fail | Fail | Fail |
| CB-011 | Navigation and browser Back | Pass | Pass | Pass | Pass |

### 10.4 Existing Defects Reproduced

**BUG-002 — Dynamic Catalog duplicate products**

- **Related test case:** CB-010
- **Browsers:** Chrome, Edge, and Firefox
- **Result:** Duplicate product entries continued to appear while scrolling the Dynamic Catalog Lazy Load section.
- **Reference:** `Bug-Reports/BUG-002.md`

**BUG-003 — Reset App State UI state inconsistency**

- **Related test case:** CB-009
- **Browsers:** Chrome, Edge, and Firefox
- **Result:** Reset App State cleared the cart and removed the cart badge, but the product button continued to display "Remove" until a page reload or navigation refreshed the product state.
- **Reference:** `Bug-Reports/BUG-003.md`

Both defects had already been documented during Phase 1. They were reproduced during Phase 2, so no duplicate defect reports were created.

### 10.5 Additional Observations

**Password visibility icon:** The password visibility icon was visible and functional in Edge but was not visible in Chrome or Firefox. Login succeeded in all three browsers. This difference was recorded as an observation, not a confirmed defect, because the expected cross-browser behavior was not established.

**Cart contents across browsers:** Products added to the cart in Chrome were not visible when accessing the application in Edge or Firefox. Cross-browser cart synchronization was not established as a requirement, so this was not classified as a defect.

**Cart product image:** The cart displayed the product name, description, price, quantity, and Remove button, but no product image was visible in any of the three browsers. CB-006 remained Pass because its stated expected result did not explicitly require a cart product image.

### 10.6 Phase 2 Conclusion

Phase 2 cross-browser execution was completed for 11 selected scenarios across Chrome, Edge, and Firefox. Nine scenarios passed and two failed across the tested browsers.

BUG-002 and BUG-003 were reproduced in all three browsers. Additional browser and cart observations were documented separately without assigning unsupported defect classifications.

Detailed browser-level results are available in `Test-Cases/Cross-Browser-Test-Matrix.xlsx`.