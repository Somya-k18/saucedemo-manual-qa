# SauceDemo Manual QA — Exploratory Test Session Report

## 1. Session Overview

**Project:** SauceDemo Manual QA 

**Test Phase:** Phase 3 — Exploratory Testing  

**Test Session ID:** ET-SESSION-01  

**Session Charter:** State, Navigation and Transaction Consistency  

**Application:** SauceDemo  

**Browser:** Google Chrome  

**Platform:** Windows  

**Testing Type:** Manual Exploratory Testing  

**Planned Time-box:** 30 minutes  

**Actual Duration:** Longer than the planned time-box; exact duration not recorded.

## 2. Objective

The objective of this exploratory session was to identify unexpected behavior involving cart state, navigation, checkout validation, and transaction consistency.

The session focused on:

- Cart state during navigation
- Changes to cart contents
- Browser Back/Forward behavior during checkout
- Checkout form validation
- Order summary consistency
- Validation boundaries
- Cart and checkout consistency after cart changes

## 3. Test Approach

Exploratory testing was performed using a structured charter. Each check involved executing a user workflow, observing the application response, and assessing whether the observed behavior was consistent with the expected workflow.

Unexpected behavior was evaluated for reproducibility and impact before being classified as a defect.

Confirmed findings were linked to a formal defect report where applicable. Inconsistent behavior without sufficient evidence was retained as an exploratory observation.

## 4. Exploratory Checks and Results

### Check 1 — Cart State After Navigation

**Objective:** Verify that cart contents remain consistent when navigating between the product catalog, product details, and cart.

**Steps Performed:**

1. Add a product to the cart.
2. Open the product details page.
3. Return to the product catalog.
4. Open the cart.
5. Verify the cart contents.

**Expected Result:**

The selected product should remain in the cart, and navigation should not unexpectedly change cart state.

**Actual Result:**

The application behaved as expected. The cart state remained consistent during the tested navigation.

**Assessment:** Passed  
**Defect ID:** None

### Check 2 — Changing Cart Contents

**Objective:** Verify that adding and removing products updates cart contents and related controls consistently.

**Steps Performed:**

1. Add two different products to the cart.
2. Open the cart.
3. Remove one product.
4. Return to the product catalog.
5. Revisit the cart.
6. Inspect the remaining product, cart badge, and product buttons.

**Expected Result:**

The removed product should no longer appear in the cart. The remaining product and cart badge should reflect the current cart state.

**Actual Result:**

The application behaved as expected during this exploratory check.

**Assessment:** Passed  
**Defect ID:** None

### Check 3 — Browser Back/Forward During Checkout

**Objective:** Observe checkout state and navigation behavior when using the browser Back and Forward buttons during checkout.

**Steps Performed:**

1. Add a product to the cart.
2. Start checkout and enter valid First Name, Last Name, and Postal Code values.
3. Continue to the Order Overview.
4. Click the browser Back button.
5. Observe the Checkout Information page and its field values.
6. Click the browser Forward button.
7. Repeat the navigation to assess reproducibility.

**Observed Results:**

- After navigating Back from the Order Overview, the Checkout Information fields appeared empty.
- The cart state remained preserved.
- During one attempt, clicking Forward displayed the message `Epic sadface: You can only access '/checkout-step-one.html' when you are logged in.` and redirected to the login page.
- During a repeated attempt, Forward reopened the Order Overview despite the Checkout Information fields appearing empty.
- The order could be completed, and the generated PDF contained the previously entered checkout information.
- Checkout information remained available during the same session but had to be entered again after logging out and logging back in.

**Assessment:**

The browser Back/Forward behavior was inconsistent. The login error occurred once and could not be reproduced consistently during repeated attempts. Its cause was not established.

**Classification:** Unconfirmed exploratory observation  
**Defect ID:** None assigned  
**Recommended Follow-up:** Revisit the behavior in a future session if it recurs. Do not classify it as a confirmed defect without consistent reproduction and clearer evidence.

### Check 4 — Checkout Form Validation

**Objective:** Determine whether required checkout fields reject whitespace-only input.

**Scenario A — All Required Fields Contain Whitespace**

**Steps Performed:**

1. Navigate to the Checkout Information page.
2. Enter whitespace-only values in First Name, Last Name, and Postal Code.
3. Click Continue.
4. Observe the result.

**Expected Result:**

The application should reject whitespace-only values and display appropriate validation messages.

**Actual Result:**

The application accepted the whitespace-only values and allowed navigation to the Order Overview.

**Scenario B — First Name Contains a Single Space**

**Steps Performed:**

1. Enter a single space in First Name.
2. Enter `KK` in Last Name.
3. Enter `302005` in Postal Code.
4. Click Continue.
5. Observe the Order Overview and generated order PDF.

**Expected Result:**

The application should reject the whitespace-only First Name and prevent continuation until a valid value is entered.

**Actual Result:**

The application allowed checkout to proceed. The generated order PDF displayed the first name as blank-looking information under Ship To, followed by the entered last name and postal code.

**Assessment:** Defect identified  
**Related Defect:** BUG-004

**Evidence:**

- `Evidence/BUG-004/BUG-004-01-Order-PDF-All-Whitespace.png`
- `Evidence/BUG-004/BUG-004-02-Order-PDF-Blank-First-Name.png`

### Check 5 — Order Summary Consistency

**Objective:** Verify that product details and calculated totals remain consistent between the cart and Order Overview.

**Steps Performed:**

1. Add one product to the cart.
2. Open the cart and note the product name, quantity, and price.
3. Start checkout.
4. Enter valid customer information.
5. Continue to the Order Overview.
6. Compare product details and calculated totals.

**Expected Result:**

The product name, quantity, price, subtotal, tax, and final total should be consistent with the selected product and displayed calculations.

**Actual Result:**

All checked product details and totals matched the expected values.

**Assessment:** Passed  
**Defect ID:** None

### Check 6 — Checkout Validation Boundaries

**Objective:** Verify that missing and whitespace-only Postal Code values are handled correctly.

**Scenario A — Postal Code Is Empty**

**Steps Performed:**

1. Enter a valid First Name and Last Name.
2. Leave Postal Code empty.
3. Click Continue.

**Expected Result:**

The application should display a validation message and prevent continuation.

**Actual Result:**

The application displayed `Error: Postal Code is required`.

**Assessment:** Passed for empty-field validation

**Scenario B — Postal Code Contains a Single Space**

**Steps Performed:**

1. Enter a valid First Name.
2. Enter a valid Last Name.
3. Enter a single space in Postal Code.
4. Click Continue.
5. Observe the Order Overview and generated order PDF.

**Expected Result:**

The application should reject the whitespace-only Postal Code and prevent continuation.

**Actual Result:**

The application accepted the single-space Postal Code and allowed navigation to the Order Overview. The generated order PDF displayed the Postal Code as blank-looking information under Ship To.

**Assessment:** Defect reproduced  
**Related Defect:** BUG-004

**Evidence:**

- `Evidence/BUG-004/BUG-004-04-Order-PDF-Blank-Postal-Code.png`

### Check 7 — Cart and Checkout Consistency After Changes

**Objective:** Verify that checkout reflects the current cart contents after a product is removed.

**Steps Performed:**

1. Add two different products to the cart.
2. Open the cart and verify both products are present.
3. Remove one product.
4. Verify the remaining product and cart badge.
5. Proceed to checkout and enter valid customer information.
6. Open the Order Overview.
7. Compare the displayed product and totals with the updated cart.

**Expected Result:**

The Order Overview should reflect only the remaining product, with the corresponding quantity and totals.

**Actual Result:**

The cart and Order Overview matched after the product was removed.

**Assessment:** Passed  

**Defect ID:** None

## 5. Session Summary

| Check | Area | Outcome |
|---|---|---|
| 1 | Cart state after navigation | Passed |
| 2 | Changing cart contents | Passed |
| 3 | Browser Back/Forward during checkout | Unconfirmed observation |
| 4 | Checkout form validation | BUG-004 identified |
| 5 | Order summary consistency | Passed |
| 6 | Checkout validation boundaries | BUG-004 reproduced |
| 7 | Cart and checkout consistency after changes | Passed |

The session covered seven exploratory checks. Four checks behaved as expected without a defect being identified. Check 3 produced inconsistent behavior that could not be confirmed as a defect. Checks 4 and 6 identified related whitespace-validation failures documented under BUG-004.

## 6. Defects Identified

### BUG-004 — Checkout Accepts Whitespace-Only Required Fields

**Module:** Checkout  

**Severity:** High

**Priority:** Medium (Provisional)

**Status:** Open

The checkout form accepts whitespace-only values in required customer information fields and allows the user to proceed to the Order Overview.

The issue was reproduced when all required fields contained whitespace, when First Name alone contained whitespace, and when Postal Code alone contained whitespace.

The generated order PDF displayed blank-looking customer information for the affected fields.

**Defect Report:** `Bug-Reports/BUG-004.md`

**Evidence Folder:** `Evidence/BUG-004/`

No additional defect ID was assigned for these related scenarios.

## 7. Unconfirmed Observations

The browser Back/Forward behavior during checkout was inconsistent. A login error occurred once but could not be reproduced consistently. The cause remains unknown.

This behavior is documented in Check 3 for future investigation and has not been classified as a confirmed defect.

## 8. Testing Limitations

- Testing was performed manually against the publicly accessible application.
- No source code or formal business requirements were available.
- The session focused on selected user workflows rather than exhaustive exploratory coverage.
- The cause of the intermittent browser navigation/login behavior was not established.
- Findings are based on the observed application behavior during this session.

## 9. Conclusion

Phase 3 exploratory testing identified a reproducible checkout validation defect involving whitespace-only required fields. The related scenarios are documented under BUG-004 with supporting PDF evidence.

Other tested workflows involving cart navigation, cart modifications, order summary calculations, and cart-to-checkout consistency behaved as expected during this session.

The inconsistent Back/Forward behavior remains an unconfirmed observation requiring further investigation if it recurs.

**Phase 3 exploratory session:** Completed  
**Formal defect identified:** BUG-004  
**Unconfirmed observation retained:** Browser Back/Forward behavior during checkout