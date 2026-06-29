# Test Cases

## Project Name

Practice Software Testing - QA Portfolio Project

## Module

Product Search

## Purpose

This document contains detailed test cases for the Product Search module.

Each test case includes test data, detailed test steps, expected results, actual results, execution status, and relevant investigation notes.

## Test Case Summary

| Status             | Count |
| ------------------ | ----: |
| Passed             |     9 |
| Failed             |     2 |
| Blocked            |     0 |
| Need Clarification |     2 |
| Total Test Cases   |    13 |

---

### TC-SEARCH-001: Search products by full product name

* Related Scenario: TS-SEARCH-001
* Module: Product Search
* Priority: High
* Test Data: Pliers
* Status: Pass

#### Test Steps

1. Open the Practice Software Testing product listing page.
2. Locate the Search section on the left side of the product listing page.
3. Click the search input field.
4. Enter `Pliers` into the search input field.
5. Click the Search button.
6. Observe the search result title.
7. Observe the displayed result count.
8. Review the names of all displayed product cards.
9. Compare the displayed result count with the number of visible product cards.

#### Expected Result

The page should display search results related to `Pliers`.

The displayed result count should match the number of visible product cards.

All displayed product names should contain or be related to the keyword `Pliers`.

#### Actual Result

The page displayed `Searched for: Pliers`.

The page displayed `4 products found for 'Pliers'`.

The displayed products were Combination Pliers, Pliers, Long Nose Pliers, and Slip Joint Pliers.

All displayed product names contained the keyword `Pliers`.

---

### TC-SEARCH-002: Search products by partial keyword

* Related Scenario: TS-SEARCH-002
* Module: Product Search
* Priority: High
* Test Data: `plier`, `ham`
* Status: Pass
* Test Cycle: Cycle 2
* Test Date: 2026-06-29

#### Test Steps

1. Open the Practice Software Testing product listing page.
2. Locate the Search section on the left side of the product listing page.
3. Click the search input field.
4. Enter `plier` into the search input field.
5. Click the Search button.
6. Record the search result title.
7. Record the displayed result count.
8. Record the names of all displayed products.
9. Click the Reset button to clear the search and restore the default product list.
10. Confirm that the search field has been cleared.
11. Enter `ham` into the search input field.
12. Click the Search button.
13. Record the search result title.
14. Record the displayed result count.
15. Record the names of all displayed products.
16. Verify whether `Sledgehammer` is included in the results.

#### Expected Result

The page should display products related to each partial keyword.

The displayed result count should be greater than 0 for valid partial keywords.

The displayed product names should contain or match the entered partial keyword regardless of letter casing.

Searching for `ham` should include products whose names contain the matching text, including `Sledgehammer`.

#### Actual Result

Searching for `plier` displayed 4 products.

The displayed products were Combination Pliers, Pliers, Long Nose Pliers, and Slip Joint Pliers.

Searching for `ham` displayed 7 products.

`Sledgehammer` was included in the `ham` search results.

Both partial keywords successfully returned related products.

#### Notes

Partial keyword search is supported and worked correctly for both `plier` and `ham`.

The `ham` result provides additional evidence that `Sledgehammer` can be returned through partial-string matching.

However, searching for `Hammer` still excludes `Sledgehammer`.

The inconsistent `Hammer` behavior remains covered by TC-SEARCH-012 and BUG-002.

---

### TC-SEARCH-003: Search with a non-existing product keyword

* Related Scenario: TS-SEARCH-003
* Module: Product Search
* Priority: Medium
* Test Data: abcdefg12345
* Status: Pass

#### Test Steps

1. Open the Practice Software Testing product listing page.
2. Locate the Search section on the left side of the product listing page.
3. Click the search input field.
4. Enter `abcdefg12345` into the search input field.
5. Click the Search button.
6. Observe the search result title.
7. Observe the displayed result count.
8. Review the product list area.
9. Check whether a no-result message is displayed.

#### Expected Result

The page should display `0 products found`.

No product cards should be displayed.

The page should display a clear no-result message.

#### Actual Result

The page displayed `Searched for: abcdefg12345`.

The page displayed `0 products found for 'abcdefg12345'`.

No product cards were displayed.

The page displayed the message `There are no products found.`

---

### TC-SEARCH-004: Reset search results

* Related Scenario: TS-SEARCH-004
* Module: Product Search
* Priority: High
* Test Data: Pliers
* Status: Pass
* Test Cycle: Cycle 2
* Test Date: 2026-06-29

#### Test Steps

1. Open the Practice Software Testing product listing page.
2. Locate the Search section on the left side of the product listing page.
3. Click the search input field.
4. Enter `Pliers` into the search input field.
5. Click the Search button.
6. Verify that the search result title is displayed.
7. Verify that Pliers-related product cards are displayed.
8. Click the Reset button.
9. Verify that the search input field is empty.
10. Verify that the search result title is no longer displayed.
11. Verify that the default product list is displayed again.
12. Verify that the default pagination controls are displayed again.

#### Expected Result

The search input field should be cleared after clicking Reset.

The active search result title should no longer be displayed.

The product list should return to the default product listing state.

Product cards and pagination should be displayed again after Reset.

#### Actual Result

After clicking Reset, the search input field was cleared.

The active search result title disappeared.

The product list returned to the default listing state.

Pagination was displayed again.

No unexpected behavior was observed.

#### Notes

Focused Exploratory Testing reconfirmed that Reset clears the active search state and restores the default product list correctly.

The result remained consistent with the earlier Cycle 2 test.

This behavior is stable, has a clear expected result, and is suitable for future Regression Testing.

---

### TC-SEARCH-005: Trigger search by pressing Enter

* Related Scenario: TS-SEARCH-005
* Module: Product Search
* Priority: High
* Test Data: Hammer
* Status: Pass

#### Test Steps

1. Open the Practice Software Testing product listing page.
2. Locate the Search section on the left side of the product listing page.
3. Click the search input field.
4. Enter `Hammer` into the search input field.
5. Press the Enter key.
6. Observe whether the search action is triggered.
7. Observe the search result title.
8. Observe the displayed result count.
9. Review the displayed product cards.

#### Expected Result

Pressing Enter should trigger the search action.

The page should display search results related to `Hammer`.

The displayed result count should match the number of visible product cards.

#### Actual Result

Pressing Enter triggered the search action.

The page displayed `Searched for: Hammer`.

The page displayed `6 products found for 'Hammer'`.

The displayed products were Claw Hammer with Shock Reduction Grip, Hammer, Claw Hammer, Thor Hammer, Claw Hammer with Fiberglass Handle, and Court Hammer.

---

### TC-SEARCH-006: Search with multiple keywords

* Related Scenario: TS-SEARCH-006
* Module: Product Search
* Priority: Low
* Test Data: Hammer Pliers
* Status: Need Clarification
* Test Cycle: Cycle 2
* Test Date: 2026-06-29

#### Test Steps

1. Open the Practice Software Testing product listing page.
2. Locate the Search section on the left side of the product listing page.
3. Click the search input field.
4. Enter `Hammer Pliers` into the search input field.
5. Click the Search button.
6. Observe the search result title.
7. Observe the displayed result count.
8. Review the product list area.
9. Check whether a no-result message is displayed.
10. Record whether the observed result appears to use exact-phrase matching, AND logic, OR logic, or unsupported multiple-keyword behavior.

#### Expected Result

The system should process multiple search keywords according to a documented and consistent search rule.

If the system uses exact-phrase matching, it should return only products matching the complete phrase.

If the system uses AND logic, it should return products matching both keywords.

If the system uses OR logic, it should return products matching either keyword.

If multiple-keyword search is unsupported, the user interface should clearly inform the user.

Until the intended rule is confirmed, the result should remain Need Clarification rather than Pass or Fail.

#### Actual Result

The page displayed `Searched for: Hammer Pliers`.

The page displayed `0 products found for 'Hammer Pliers'`.

No product cards were displayed.

The page displayed the message `There are no products found.`

The observed behavior may indicate exact-phrase matching or unsupported multiple-keyword input.

The intended search rule cannot be confirmed from the current requirements.

#### Notes

The product requirement does not define whether multiple keywords should use AND logic, OR logic, exact-phrase matching, or unsupported behavior.

The current result must not be classified as a Functional Bug until the expected behavior is confirmed.

The intended search rule should be confirmed with the Product Owner, Product Manager, Business Analyst, or requirement documentation.

If multiple-keyword input is unsupported, the user interface should provide a clear instruction or validation message.

---

### TC-SEARCH-007: Search with different letter casing

* Related Scenario: TS-SEARCH-007
* Module: Product Search
* Priority: Medium
* Test Data: `Hammer`, `hammer`, `HAMMER`
* Status: Pass
* Test Cycle: Cycle 2
* Test Date: 2026-06-29

#### Test Steps

1. Open the Practice Software Testing product listing page.
2. Locate the Search section on the left side of the product listing page.
3. Click the search input field.
4. Enter `Hammer` into the search input field.
5. Click the Search button.
6. Record the result count and displayed product names.
7. Click Reset to clear the search and restore the default product list.
8. Enter `hammer` into the search input field.
9. Click the Search button.
10. Record the result count and displayed product names.
11. Click Reset again.
12. Enter `HAMMER` into the search input field.
13. Click the Search button.
14. Record the result count and displayed product names.
15. Compare the result counts and displayed product names from all three searches.

#### Expected Result

The search should be case-insensitive.

Searching for `Hammer`, `hammer`, and `HAMMER` should return the same result count.

All three searches should return the same product list.

The displayed products should be related to the Hammer keyword.

#### Actual Result

Searching for `Hammer`, `hammer`, and `HAMMER` returned the same 6 products.

The displayed products were Claw Hammer with Shock Reduction Grip, Hammer, Claw Hammer, Thor Hammer, Claw Hammer with Fiberglass Handle, and Court Hammer.

The result count and product names were consistent across all three letter-case variations.

#### Notes

Focused Exploratory Testing confirmed that Product Search handles uppercase, lowercase, and title-case keywords consistently.

The result remained consistent with the earlier Cycle 2 test.

This behavior is stable and suitable for future Regression Testing.

---

### TC-SEARCH-008: Search with leading and trailing spaces

* Related Scenario: TS-SEARCH-008
* Module: Product Search
* Priority: Medium
* Test Data: `[space]Hammer`, `Hammer[space]`, `[space]Hammer[space]`, `Hammer`
* Status: Pass
* Test Cycle: Cycle 2
* Test Date: 2026-06-29

#### Test Steps

1. Open the Practice Software Testing product listing page.
2. Locate the Search section on the left side of the product listing page.
3. Click the search input field.
4. Enter one leading space followed by `Hammer`.
5. Click the Search button.
6. Record the result count and displayed product names.
7. Click Reset to clear the search and restore the default product list.
8. Enter `Hammer` followed by one trailing space.
9. Click the Search button.
10. Record the result count and displayed product names.
11. Click Reset again.
12. Enter one leading space, `Hammer`, and one trailing space.
13. Click the Search button.
14. Record the result count and displayed product names.
15. Click Reset again.
16. Enter `Hammer` without any extra spaces.
17. Click the Search button.
18. Record the result count and displayed product names.
19. Compare the result counts and product names from all four searches.

#### Expected Result

The system should ignore leading and trailing spaces in the search keyword.

Searching with a leading space, a trailing space, or both leading and trailing spaces should return the same result count and product list as searching for `Hammer` without spaces.

The search should not fail only because extra spaces appear before or after the keyword.

#### Actual Result

Searching with one leading space before `Hammer`, one trailing space after `Hammer`, and spaces on both sides returned the same 6 products as searching for `Hammer` without spaces.

The result counts and displayed product names were identical in all four searches.

The system successfully ignored the extra leading and trailing spaces.

#### Notes

Focused Exploratory Testing confirmed that Product Search trims leading and trailing spaces consistently.

The behavior remained consistent with the earlier Cycle 2 test.

This is stable behavior with a clear expected result and is suitable for future Regression Testing.

---

### TC-SEARCH-009: Search with localized keyword

* Related Scenario: TS-SEARCH-009
* Module: Product Search
* Priority: Low
* Test Data: 鉗子
* Status: Need Clarification

#### Test Steps

1. Open the Practice Software Testing product listing page.
2. Locate the Search section on the left side of the product listing page.
3. Click the search input field.
4. Enter `鉗子` into the search input field.
5. Click the Search button.
6. Observe the search result title.
7. Observe the displayed result count.
8. Review the product list area.
9. Check whether a no-result message is displayed.
10. Compare the behavior with a non-existing English keyword search.

#### Expected Result

The expected behavior for localized keyword search is not clearly defined.

The requirement should clarify whether localized keyword search is supported.

If localized search is not supported, the system should still provide clear feedback or consistent no-result behavior.

#### Actual Result

The search input accepted the localized keyword `鉗子`.

After clicking the Search button, the page did not display `Searched for: 鉗子`.

The page did not display `0 products found for '鉗子'`.

The page did not display a no-result message.

The product list remained in the default product listing view.

#### Notes

The current behavior is different from searching with a non-existing English keyword.

The expected behavior should be confirmed before this test case is marked as Pass or Fail.

---

### TC-SEARCH-010: Search with category filter

* Related Scenario: TS-SEARCH-010
* Module: Product Search
* Priority: Medium
* Test Data: Hammer category filter and search keyword `hammer`
* Status: Fail
* Test Cycle: Cycle 2
* Test Date: 2026-06-29

#### Precondition

The user is on the Practice Software Testing product listing page.

No search keyword is currently active.

#### Test Steps

1. Open the Practice Software Testing product listing page.
2. Locate the Filters section on the left side of the page.
3. Locate the By category section.
4. Expand Hand Tools if the category list is collapsed.
5. Select the Hammer category checkbox.
6. Wait for the filtered product list to load.
7. Verify that 7 Hammer-category products are displayed.
8. Verify that `Sledgehammer` is included in the category-filtered results.
9. Keep the Hammer category checkbox selected.
10. Locate the Search section on the left side of the page.
11. Enter `hammer` into the search input field.
12. Click the Search button.
13. Wait for the combined filter results to load.
14. Record the displayed result count.
15. Record the names of all displayed products.
16. Verify whether `Sledgehammer` remains included in the combined results.

#### Expected Result

The page should display products that satisfy both the selected Hammer category and the search keyword `hammer`.

All matching Hammer-category products whose names contain `hammer` should be displayed.

`Sledgehammer` should be included in the combined results.

#### Actual Result

With the Hammer category filter selected, the page initially displayed 7 products, including `Sledgehammer`.

After entering `hammer` while keeping the Hammer category selected, the page displayed only 6 products.

`Sledgehammer` was not included in the combined search and category filter results.

The combined filtering result was incomplete.

#### Notes

The Hammer category filter independently displayed 7 products, including `Sledgehammer`.

When `hammer` was searched while the Hammer category remained selected, only 6 products were displayed.

The missing product behavior is related to the Search API result rather than the category data.

Related bug: BUG-002.

---

### TC-SEARCH-011: Verify pagination after searching

* Related Scenario: TS-SEARCH-011
* Module: Product Search
* Priority: Medium
* Test Data: Pliers
* Status: Pass
* Test Cycle: Cycle 2
* Test Date: 2026-06-29

#### Test Steps

1. Open the Practice Software Testing product listing page.
2. Confirm that the default product list and pagination are displayed.
3. Locate the Search section on the left side of the product listing page.
4. Enter `Pliers` into the search input field.
5. Click the Search button.
6. Wait for the search results to load.
7. Observe the displayed result count.
8. Count the visible product cards.
9. Check whether pagination is displayed after the search results are loaded.
10. Compare the pagination state with the number of search results.

#### Expected Result

The page should display Pliers-related products.

If all search results fit on one page, pagination should not be displayed.

Pagination should update correctly according to the number of search results.

#### Actual Result

The page displayed `4 products found for 'Pliers'`.

All displayed products were related to Pliers.

No pagination was displayed after the search results loaded.

The search results fit on one page.

#### Notes

The result remained consistent during Cycle 2.

No issue was identified.

---

### TC-SEARCH-012: Verify that searching for Hammer includes Sledgehammer

* Related Scenario: TS-SEARCH-002
* Module: Product Search
* Priority: High
* Test Data: `Hammer`, `ham`
* Status: Fail
* Test Cycle: Cycle 2
* Test Date: 2026-06-29

#### Precondition

The user is on the Practice Software Testing product listing page.

No category filter is selected.

Chrome DevTools is available for Network request inspection.

#### Test Steps

1. Open the Practice Software Testing product listing page.
2. Confirm that no category filter is selected.
3. Locate the Search section on the left side of the product listing page.
4. Enter `Hammer` into the search input field.
5. Click the Search button.
6. Wait for the search results to load.
7. Record the displayed result count.
8. Record the names of all displayed products.
9. Verify whether `Sledgehammer` is included in the UI results.
10. Open Chrome DevTools by pressing F12.
11. Select the Network tab.
12. Repeat the search for `Hammer`.
13. Select the GET request to `/products/search?q=Hammer`.
14. Inspect the response body.
15. Verify whether the API response includes `Sledgehammer`.
16. Click Reset to clear the search and restore the default product list.
17. Enter `ham` into the search input field.
18. Click the Search button.
19. Wait for the search results to load.
20. Record the displayed result count.
21. Verify whether `Sledgehammer` is included in the `ham` results.
22. Compare the results for `Hammer` and `ham`.

#### Expected Result

Searching for `Hammer` should return all products whose names contain the matching search text, including `Sledgehammer`.

The UI should display 7 matching products.

The Search API response should include `Sledgehammer`.

Searching for the related partial keyword `ham` should follow the same documented matching rule and return consistent results.

#### Actual Result

Searching for `Hammer` returned only 6 products.

`Sledgehammer` was not included in the UI results.

The API response for `q=Hammer` returned a total of 6 products and did not include `Sledgehammer`.

Searching for `ham` returned 7 products and included `Sledgehammer`.

The results were inconsistent because the shorter partial keyword `ham` found `Sledgehammer`, while `Hammer` did not.

#### Notes

Additional Exploratory Testing confirmed that partial-string searching is supported because `ham` successfully returned 7 products, including `Sledgehammer`.

The new evidence suggests an inconsistency in the backend search matching logic rather than a general lack of partial-string support.

This test verifies the search function without any category filter selected.

Related bug: BUG-002.

---

### TC-SEARCH-013: Verify that the Hammer category filter displays all Hammer-category products

* Related Scenario: TS-SEARCH-012
* Module: Product Search
* Priority: High
* Test Data: Hammer category
* Status: Pass
* Test Cycle: Cycle 2
* Test Date: 2026-06-29

#### Precondition

The user is on the Practice Software Testing product listing page.

No search keyword is currently active.

#### Test Steps

1. Open the Practice Software Testing product listing page.
2. Locate the Filters section on the left side of the page.
3. Locate the By category section.
4. Expand Hand Tools if the category list is collapsed.
5. Select the Hammer category checkbox.
6. Wait for the filtered product list to load.
7. Record the displayed result count.
8. Record the names of all displayed products.
9. Verify that 7 Hammer-category products are displayed.
10. Verify that `Sledgehammer` is included in the results.

#### Expected Result

The page should display 7 products belonging to the Hammer category.

`Sledgehammer` should be included in the displayed results.

#### Actual Result

The page displayed 7 products after selecting the Hammer category filter.

`Sledgehammer` was included in the displayed results.

#### Notes

This test verifies the Hammer category filter independently from the search function.

The category data and frontend display can return `Sledgehammer` correctly.

No issue was identified.
