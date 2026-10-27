# SauceDemo Manual QA — Test Execution Report

## 1. Execution Overview

**Project:** SauceDemo Manual QA Testing  
**Testing Phases Covered:** Phase 1 — Functional Testing; Phase 2 — Cross-Browser Testing; Phase 3 — Exploratory Testing; Phase 4 — Responsive Compatibility Testing  
**Application:** SauceDemo Web Application  
**Test Type:** Manual Testing  
**Execution Status:** Phases 1–4 completed  
**Phase 1 Test Cases Executed:** 39  
**Phase 2 Browser-Level Executions:** 33  
**Phase 3 Exploratory Checks:** 7  
**Phase 4 Viewport-Level Executions:** 36

This report presents phase-specific results separately. The execution totals represent different testing units and should not be combined into a single pass rate.

## 2. Test Environment

- **Operating System:** Windows
- **Application:** SauceDemo Web Application
- **Phase 1 Primary Browser:** Google Chrome
- **Phase 1 Browser Coverage:** Functional test execution was performed in Chrome.
- **Phase 2 Browser Coverage:** Google Chrome, Microsoft Edge, and Mozilla Firefox.
- **Phase 4 Viewports:** Desktop (1366 × 768), Tablet (768 × 1024), and Mobile (390 × 844).
- **Test Data:** SauceDemo standard and predefined user accounts, along with valid and invalid checkout data as applicable to individual test cases.
- **Testing Limitation:** Phase 4 evaluated responsive web layouts; it did not test a native mobile application.

## 3. Phase 1 — Functional Test Execution Summary

| Result | Count |
|---|---:|
| Total Test Cases | 39 |
| Passed | 36 |
| Failed | 3 |
| Blocked | 0 |
| Not Executed | 0 |
| **Pass Rate** | **92.3%** |

The pass rate is calculated for the Phase 1 functional suite only.

## 4. Phase 1 — Module-wise Execution Results

| Module | Total | Passed | Failed |
|---|---:|---:|---:|
| Authentication | 7 | 7 | 0 |
| Products | 8 | 8 | 0 |
| Cart | 7 | 7 | 0 |
| Checkout | 7 | 7 | 0 |
| Navigation & Session | 6 | 4 | 2 |
| Dynamic Catalog | 4 | 3 | 1 |
| **Total** | **39** | **36** | **3** |

## 5. Phase 1 — Failed Test Cases

### TC-NAV-005 — Prolonged Inactivity / Session Expiration

**Status:** Failed  
**Defect:** BUG-001

After a period of inactivity, the session became invalid and the application displayed page-specific authentication error messages when accessing protected routes, including `/inventory.html` and `/cart.html`.

**Defect Report:** `Bug-Reports/BUG-001.md`

---

### TC-NAV-006 — Reset App State

**Status:** Failed  
**Defect:** BUG-003

Reset App State cleared the cart and removed the cart badge, but the product button continued to display **Remove** even though the product was no longer in the cart. The button returned to **Add to cart** after a page reload or navigation that refreshed the product catalog.

Further testing also confirmed that when Reset App State was selected from the cart page, the cart badge disappeared but the previously added item remained visible on that page.

**Defect Report:** `Bug-Reports/BUG-003.md`

---

### TC-DYN-003 — Dynamic Catalog Duplicate Products

**Status:** Failed  
**Defect:** BUG-002

The Dynamic Catalog Lazy Load section continuously generated duplicate product entries while scrolling.

**Defect Report:** `Bug-Reports/BUG-002.md`

## 6. Defects Identified

The following defect classifications reflect the impact criteria documented for this portfolio project. BUG-004's priority and BUG-006's severity and priority remain provisional pending final assessment against the project's classification criteria.

| Defect ID | Related Test / Check | Module | Severity | Priority | Status |
|---|---|---|---|---|---|
| BUG-001 | TC-NAV-005 | Navigation & Session | Medium | Medium | Open |
| BUG-002 | TC-DYN-003; CB-010; RC-012 | Dynamic Catalog | Medium | Medium | Open |
| BUG-003 | TC-NAV-006; CB-009; RC-011 | Navigation & Session | Medium | Medium | Open |
| BUG-004 | Exploratory Checks 4 and 6; RC-007 | Checkout | High | Medium (Provisional) | Open |
| BUG-005 | RC-012 | Dynamic Catalog | Medium | Medium | Open |
| BUG-006 | RC-002 | Authentication / Responsive Compatibility | Medium (Provisional) | Medium (Provisional) | Open |
| BUG-007 | RC-003 | Product Catalog / Responsive Compatibility | Medium (Provisional) | Medium (Provisional) | Open |

### BUG-006 Summary

The invalid-credentials error message is partially clipped and not fully readable within the red error container on desktop and mobile viewports. The issue was not observed on the tablet viewport during testing.

**Defect Report:** `Bug-Reports/BUG-006.md`

### BUG-007 Summary

Excessive vertical spacing in mobile product cards pushes the price and Add to Cart controls farther down the page, requiring users to scroll to reach them. The issue was not observed on the tested desktop and tablet viewports.

**Defect Report:** `Bug-Reports/BUG-007.md`

The severity and priority for BUG-007 are provisional until the impact assessment is finalized. Update the values if your completed defect report assigns different classifications.

## 7. Evidence

Evidence captured during testing is stored in the following repository directories:

- `Evidence/BUG-001/`
- `Evidence/BUG-002/`
- `Evidence/BUG-003/`
- `Evidence/BUG-004/`
- `Evidence/BUG-005/`
- `Evidence/Responsive-Compatibility/` — responsive screenshots captured for the tested scenarios and viewports.

The responsive compatibility evidence should be traceable to the corresponding RC scenario IDs and viewport sizes. Defect reports and test matrices should identify the exact supporting screenshot filenames.

For BUG-006, include the verified desktop and mobile RC-002 screenshot filenames in `Bug-Reports/BUG-006.md`. Do not identify the tablet screenshot as evidence of the clipping defect.

For BUG-007, include the verified mobile RC-003 screenshot filename in `Bug-Reports/BUG-007.md`.

## 8. Additional Observations

During testing, several application behaviors were observed but were not classified as confirmed defects because the expected behavior or applicable requirement had not been established.

- **Dynamic Catalog interaction limitations:** The Spinner subsection displayed product entries without visible spinning or movement, and some Dynamic Catalog sections provided limited product details and no Add to Cart option.
- **Cart quantity-control behavior:** The cart did not provide quantity adjustment controls. The product button changed from **Add to cart** to **Remove** after selection, and the same product could not be added again while selected.
- **About-page navigation:** Selecting About redirected the user to the Sauce Labs website. Returning to the application required using the browser's Back function.
- **Checkout with an empty cart:** The application allowed checkout to proceed and an order to be completed with no products in the cart, resulting in a total of $0.00.
- **Browser Back/Forward behavior:** Inconsistent behavior was observed during checkout but could not be reproduced consistently.

These findings remain observations rather than confirmed defects because sufficient evidence of a requirement violation had not been established. Confirmed defects are documented separately in Section 6 and their corresponding defect reports.

## 9. Phase 1 — Functional Testing Conclusion

Phase 1 functional testing was completed with all **39 planned functional test cases executed**. A total of **36 test cases passed** and **3 failed**, resulting in a **92.3% pass rate** for the functional suite.

Three defects were documented during Phase 1:

- **BUG-001** — Session expiration error handling
- **BUG-002** — Dynamic Catalog duplicate products
- **BUG-003** — Reset App State UI state inconsistency

The Phase 1 results represent functional testing in Chrome only. Cross-browser, exploratory, and responsive compatibility results are documented separately below.

---

## 10. Phase 2 — Cross-Browser Test Execution

### 10.1 Execution Overview

| Metric | Result |
|---|---:|
| Browsers Tested | 3 |
| Cross-Browser Scenarios | 11 |
| Total Browser-Level Executions | 33 |
| Scenarios Passed in All Three Browsers | 9 |
| Scenarios Failed in All Three Browsers | 2 |
| Blocked Scenarios | 0 |
| Not Executed Scenarios | 0 |

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
- **Result:** Reset App State cleared the cart and removed the cart badge, but the product button continued to display **Remove** until a page reload or navigation refreshed the product state.
- **Reference:** `Bug-Reports/BUG-003.md`

Both defects had already been documented during Phase 1. They were reproduced during Phase 2, so no duplicate defect reports were created.

### 10.5 Additional Observations

**Password visibility icon:** The password visibility icon was visible and functional in Edge but was not visible in Chrome or Firefox. Login succeeded in all three browsers. This difference was recorded as an observation, not a confirmed defect, because the expected cross-browser behavior was not established.

**Cart contents across browsers:** Products added to the cart in Chrome were not visible when accessing the application in Edge or Firefox during the recorded test. Cross-browser cart synchronization was not established as a requirement, so this was not classified as a defect.

**Cart product image:** The cart displayed the product name, description, price, quantity, and Remove button, but no product image was visible in any of the three browsers. CB-006 remained Pass because its stated expected result did not explicitly require a cart product image.

### 10.6 Phase 2 Conclusion

Phase 2 cross-browser execution was completed for 11 selected scenarios across Chrome, Edge, and Firefox. Nine scenarios passed and two failed across the tested browsers.

BUG-002 and BUG-003 were reproduced in all three browsers. Additional browser and cart observations were documented separately without assigning unsupported defect classifications.

Detailed browser-level results are available in `Test-Cases/Cross-Browser-Test-Matrix.xlsx`.

---

## 11. Phase 3 — Exploratory Test Execution

**Session ID:** ET-SESSION-01  
**Charter:** State, Navigation and Transaction Consistency  
**Status:** Completed  
**Planned Time-box:** 30 minutes  
**Actual Duration:** Longer than the planned time-box; exact duration not recorded.

Seven exploratory checks were performed to examine cart state, checkout navigation, form validation, order summary accuracy, and transaction consistency.

### 11.1 Summary of Findings

| Finding | Result |
|---|---|
| Cart state after navigation | No issue identified |
| Changing cart contents | No issue identified |
| Browser Back/Forward during checkout | Inconsistent behavior observed; unconfirmed |
| Whitespace-only checkout fields | Failed — BUG-004 |
| Order summary consistency | Passed |
| Checkout validation boundaries | Failed — BUG-004 |
| Cart and checkout consistency after changes | Passed |

### 11.2 Defect Identified

**BUG-004 — Checkout Accepts Whitespace-Only Required Fields**

Whitespace-only values were accepted in required checkout fields, allowing the user to proceed to Order Overview. The generated order PDF displayed blank-looking values for the affected fields. Testing confirmed that the order could be completed and a receipt generated when all required fields contained whitespace-only values.

- **Severity:** High
- **Priority:** Medium (Provisional)
- **Defect Report:** `Bug-Reports/BUG-004.md`
- **Evidence:** `Evidence/BUG-004/`

### 11.3 Unconfirmed Observation

Inconsistent browser Back/Forward behavior was observed during checkout. Checkout fields appeared empty after navigating backward, and one attempt produced a page-specific authentication error when navigating forward. The behavior was not reproduced consistently and was not classified as a confirmed defect.

### 11.4 Phase 3 Conclusion

Phase 3 exploratory testing was completed. Seven checks were performed, and one confirmed defect, BUG-004, was documented. An additional navigation observation remains unconfirmed.

Detailed steps, observations, and supporting evidence are recorded in `Test-Execution/Exploratory-Test-Session-Report.md`.

---

## 12. Phase 4 — Responsive Compatibility Test Execution

### 12.1 Execution Overview

| Metric | Result |
|---|---:|
| Responsive Test Scenarios | 12 |
| Viewports Tested | 3 |
| Total Viewport-Level Executions | 36 |
| Desktop Viewport | 1366 × 768 |
| Tablet Viewport | 768 × 1024 |
| Mobile Viewport | 390 × 844 |

The 12 responsive compatibility scenarios were evaluated across desktop, tablet, and mobile viewport sizes, resulting in 36 viewport-level executions. These are responsive web tests, not native mobile application tests.

Detailed results are recorded in `Test-Cases/Responsive-Compatibility-Test-Matrix.xlsx`, sheet `Responsive Test Matrix`.

### 12.2 Defects Reproduced

**BUG-003 — Reset App State UI state inconsistency**

- **Related test case:** RC-011
- **Result:** The Reset App State inconsistency was reproduced during responsive compatibility testing.
- **Reference:** `Bug-Reports/BUG-003.md`
- **Evidence location:** `Evidence/Responsive-Compatibility/`

**BUG-002 — Dynamic Catalog duplicate products**

- **Related test case:** RC-012
- **Result:** Duplicate product entries continued to appear while scrolling the Dynamic Catalog.
- **Reference:** `Bug-Reports/BUG-002.md`
- **Evidence location:** `Evidence/Responsive-Compatibility/`

**BUG-005 — Dynamic Catalog images are clipped**

- **Related test case:** RC-012
- **Result:** Images were clipped in the Lazy Load, Spinner, and Slider sections across the tested desktop, tablet, and mobile viewports.
- **Reference:** `Bug-Reports/BUG-005.md`
- **Evidence location:** `Evidence/Responsive-Compatibility/`

**BUG-004 — Checkout accepts whitespace-only required fields**

- **Related test case:** RC-007
- **Result:** The whitespace-only checkout validation issue was reproduced during responsive compatibility testing.
- **Reference:** `Bug-Reports/BUG-004.md`
- **Evidence location:** `Evidence/Responsive-Compatibility/`

**BUG-006 — Invalid-credentials error message is partially clipped**

- **Related test case:** RC-002
- **Module:** Authentication / Responsive Compatibility
- **Affected viewports:** Desktop (1366 × 768) and Mobile (390 × 844)
- **Unaffected viewport:** Tablet (768 × 1024), based on recorded testing
- **Result:** The invalid-credentials error message was partially clipped and not fully readable within the red error container on desktop and mobile. The issue was not observed on tablet.
- **Reference:** `Bug-Reports/BUG-006.md`
- **Evidence location:** `Evidence/Responsive-Compatibility/`

**BUG-007 — Excessive vertical spacing in mobile product cards**

- **Related test case:** RC-003
- **Module:** Product Catalog / Responsive Compatibility
- **Affected viewport:** Mobile (390 × 844)
- **Unaffected viewports:** Desktop (1366 × 768) and Tablet (768 × 1024), based on recorded testing
- **Result:** Excessive vertical spacing between product descriptions and the price/Add to Cart controls pushes these controls farther down the page, requiring users to scroll to reach them.
- **Reference:** `Bug-Reports/BUG-007.md`
- **Evidence location:** `Evidence/Responsive-Compatibility/`

The desktop and mobile screenshots for BUG-006 and the mobile screenshot for BUG-007 should be identified by their actual filenames in the corresponding defect reports. Severity and priority classifications should be finalized in accordance with the project criteria.

### 12.3 Additional Observations

The following responsive observations were recorded for further review. They are not listed as confirmed defects in this report:

- **RC-001:** Accepted-user information extends below the initial mobile viewport; scroll accessibility requires further investigation.
- **RC-004:** Product sorting resets when returning from the cart; the expected behavior has not been established.

RC-002 and RC-003 are documented as defects under BUG-006 and BUG-007, respectively, rather than remaining unclassified observations.

### 12.4 Phase 4 Conclusion

Responsive compatibility testing was completed for 12 scenarios across three viewport sizes, for 36 viewport-level executions. BUG-002, BUG-003, BUG-004, BUG-005, BUG-006, and BUG-007 were linked to their relevant responsive checks where recorded.

BUG-006 affects desktop and mobile viewports; the issue was not observed on tablet. BUG-007 affects the mobile product catalog layout; the issue was not observed on the tested desktop and tablet viewports.

Additional responsive observations were documented for follow-up rather than automatically classified as defects.

The results cover responsive web layouts at the listed viewport sizes and do not establish compatibility with native mobile applications or every possible screen size.

---

## 13. Overall Execution Conclusion

The four testing phases documented in this report have been completed:

- **Phase 1 — Functional Testing:** 39 test cases executed; 36 passed and 3 failed; 92.3% pass rate.
- **Phase 2 — Cross-Browser Testing:** 11 scenarios executed across Chrome, Edge, and Firefox, for 33 browser-level executions; 9 scenarios passed and 2 failed across all three browsers.
- **Phase 3 — Exploratory Testing:** 7 checks completed; BUG-004 documented; one additional navigation observation remains unconfirmed.
- **Phase 4 — Responsive Compatibility Testing:** 12 scenarios evaluated across desktop, tablet, and mobile viewports, for 36 viewport-level executions. BUG-006 and BUG-007 were documented for the login error-message clipping and mobile product-card spacing issues, respectively.

**Seven defect reports are listed: BUG-001 through BUG-007.**

Defect severity and priority reflect the criteria defined for this portfolio project. BUG-004's priority remains provisional. BUG-006 and BUG-007's severity and priority should be finalized against the project criteria.

Phase-specific metrics are reported separately because test cases, browser-level executions, exploratory checks, and viewport-level executions are different units and should not be combined into a single overall pass rate.