# Test Cases

## Project Name

Practice Software Testing - QA Portfolio Project

## Module

Product Search

## Purpose

This document contains detailed test cases for the Product Search module.

Each test case includes test data, test steps, expected result, actual result, and execution status.

## Test Case Summary

| Status | Count |
|---|---:|
| Passed | 8 |
| Failed | 0 |
| Blocked | 1 |
| Need Clarification | 2 |
| Total Test Cases | 11 |

## Test Case List

### TC-SEARCH-001: Search products by full product name

- Related Scenario: TS-SEARCH-001
- Module: Product Search
- Priority: High
- Test Data: Pliers
- Status: Pass

#### Test Steps

1. Open the product listing page.
2. Locate the search input field at the top of the product list.
3. Enter `Pliers` into the search input field.
4. Click the Search button.
5. Observe the search result title, result count, and displayed product cards.

#### Expected Result

The page should display search results related to `Pliers`.

The result count should match the number of displayed products.

All displayed product names should contain or be related to the keyword `Pliers`.

#### Actual Result

The page displayed `Searched for: Pliers`.

The page displayed `4 products found for 'Pliers'`.

The displayed products were Combination Pliers, Pliers, Long Nose Pliers, and Slip Joint Pliers.

All displayed product names contained the keyword `Pliers`.

---

### TC-SEARCH-002: Search products by partial keyword

- Related Scenario: TS-SEARCH-002
- Module: Product Search
- Priority: High
- Test Data: plier
- Status: Pass

#### Test Steps

1. Open the product listing page.
2. Locate the search input field at the top of the product list.
3. Enter `plier` into the search input field.
4. Click the Search button.
5. Observe the search result title, result count, and displayed product cards.

#### Expected Result

The page should display products related to the partial keyword `plier`.

The search behavior should support partial keyword matching.

The displayed products should match the expected Pliers-related results.

#### Actual Result

The page displayed the same product results as searching for `Pliers`.

4 products were displayed.

The displayed products were Combination Pliers, Pliers, Long Nose Pliers, and Slip Joint Pliers.

Search appears case-insensitive and partial keyword search works correctly.

---

### TC-SEARCH-003: Search with a non-existing product keyword

- Related Scenario: TS-SEARCH-003
- Module: Product Search
- Priority: Medium
- Test Data: abcdefg12345
- Status: Pass

#### Test Steps

1. Open the product listing page.
2. Locate the search input field at the top of the product list.
3. Enter `abcdefg12345` into the search input field.
4. Click the Search button.
5. Observe the search result title, result count, product list area, and no-result message.

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

- Related Scenario: TS-SEARCH-004
- Module: Product Search
- Priority: High
- Test Data: Pliers
- Status: Pass

#### Test Steps

1. Open the product listing page.
2. Locate the search input field at the top of the product list.
3. Enter `Pliers` into the search input field.
4. Click the Search button.
5. Verify that Pliers-related search results are displayed.
6. Click the Reset button.
7. Observe the search input field, search result title, product list, and pagination.

#### Expected Result

The search field should be cleared.

The search result title should no longer be displayed.

The product list should return to the default product listing view.

Pagination should be displayed again after reset.

#### Actual Result

The search field was cleared after clicking the Reset button.

The search result title `Searched for: Pliers` was no longer displayed.

The product list returned to the default product listing view.

Pagination was displayed again after reset.

---

### TC-SEARCH-005: Trigger search by pressing Enter

- Related Scenario: TS-SEARCH-005
- Module: Product Search
- Priority: High
- Test Data: Hammer
- Status: Pass

#### Test Steps

1. Open the product listing page.
2. Locate the search input field at the top of the product list.
3. Enter `Hammer` into the search input field.
4. Press the Enter key.
5. Observe the search result title, result count, and displayed product cards.

#### Expected Result

Pressing Enter should trigger the search action.

The page should display search results related to `Hammer`.

The result count should match the number of displayed products.

#### Actual Result

Pressing Enter triggered the search action.

The page displayed `Searched for: Hammer`.

The page displayed `6 products found for 'Hammer'`.

Displayed products were Claw Hammer with Shock Reduction Grip, Hammer, Claw Hammer, Thor Hammer, Claw Hammer with Fiberglass Handle, and Court Hammer.

---

### TC-SEARCH-006: Search with multiple keywords

- Related Scenario: TS-SEARCH-006
- Module: Product Search
- Priority: Low
- Test Data: Hammer Pliers
- Status: Need Clarification

#### Test Steps

1. Open the product listing page.
2. Locate the search input field at the top of the product list.
3. Enter `Hammer Pliers` into the search input field.
4. Click the Search button.
5. Observe the search result title, result count, product list area, and no-result message.

#### Expected Result

The expected behavior is not clearly defined.

Need to clarify whether multiple keyword search should use AND logic, OR logic, exact phrase search, or unsupported behavior.

#### Actual Result

The page displayed `Searched for: Hammer Pliers`.

The page displayed `0 products found for 'Hammer Pliers'`.

No product cards were displayed.

The page displayed the message `There are no products found.`

The current behavior appears to treat `Hammer Pliers` as an exact phrase search.

#### Notes

This test case should be confirmed with PM / PO / BA before marking it as Pass or Fail.

---

### TC-SEARCH-007: Search with different letter casing

- Related Scenario: TS-SEARCH-007
- Module: Product Search
- Priority: Medium
- Test Data: hammer
- Status: Pass

#### Test Steps

1. Open the product listing page.
2. Locate the search input field at the top of the product list.
3. Enter `hammer` in lowercase into the search input field.
4. Click the Search button.
5. Observe the search result title, result count, and displayed product cards.

#### Expected Result

The search should not be affected by keyword letter casing.

Searching for `hammer` should return the same results as searching for `Hammer`.

The page should display Hammer-related products.

#### Actual Result

The page displayed `Searched for: hammer`.

The page displayed the same product results as TC-SEARCH-005 using `Hammer`.

The page displayed 6 Hammer-related products.

Displayed products were Claw Hammer with Shock Reduction Grip, Hammer, Claw Hammer, Thor Hammer, Claw Hammer with Fiberglass Handle, and Court Hammer.

#### Notes

Search behavior appears case-insensitive.

---

### TC-SEARCH-008: Search with leading and trailing spaces

- Related Scenario: TS-SEARCH-008
- Module: Product Search
- Priority: Medium
- Test Data: ` hammer `
- Status: Pass

#### Test Steps

1. Open the product listing page.
2. Locate the search input field at the top of the product list.
3. Enter ` hammer ` into the search input field with one leading space and one trailing space.
4. Click the Search button.
5. Observe the search result title, result count, and displayed product cards.
6. Compare the results with TC-SEARCH-007.

#### Expected Result

The search input should handle leading and trailing spaces correctly.

The result should not be affected by extra spaces before or after the keyword.

Searching for ` hammer ` should return the same results as searching for `hammer`.

#### Actual Result

The page handled the input with one leading space and one trailing space.

The search results were the same as searching for `hammer` without spaces.

The page displayed 6 Hammer-related products.

The displayed products matched the results from TC-SEARCH-007.

#### Notes

The actual input is ` hammer ` with one leading space and one trailing space.

This test verifies whether the search input trims leading and trailing spaces.

The search input appears to trim leading and trailing spaces.

No issue found.

---

### TC-SEARCH-009: Search with localized keyword

- Related Scenario: TS-SEARCH-009
- Module: Product Search
- Priority: Low
- Test Data: 鉗子
- Status: Need Clarification

#### Test Steps

1. Open the product listing page.
2. Locate the search input field at the top of the product list.
3. Enter `鉗子` into the search input field.
4. Click the Search button.
5. Observe the search result title, result count, product list area, and no-result message.

#### Expected Result

The expected behavior for localized keyword search is not clearly defined.

Need to clarify whether localized keyword search should be supported.

If localized search is not supported, the system should still provide clear feedback or consistent no-result behavior.

#### Actual Result

The search input accepted the localized keyword `鉗子`.

After clicking the Search button, the page did not display `Searched for: 鉗子`.

The page did not display `0 products found for '鉗子'`.

The page did not display a no-result message.

The product list remained in the default product listing view.

#### Notes

Current behavior is different from searching a non-existing English keyword.

This test case should be confirmed with PM / PO / BA before marking it as Pass or Fail.

---

### TC-SEARCH-010: Search with category filter

- Related Scenario: TS-SEARCH-010
- Module: Product Search
- Priority: Medium
- Test Data: Hammer category filter
- Status: Blocked

#### Test Steps

1. Open the product listing page.
2. Locate the Filters section on the left side of the page.
3. Under By category, find Hand Tools.
4. Select the Hammer category checkbox.
5. Observe the product list.
6. If Hammer-related products are displayed, enter a Hammer-related keyword in the search input field.
7. Click the Search button.
8. Observe whether the search keyword and category filter work together correctly.

#### Expected Result

After selecting the Hammer category filter, the page should display Hammer-related products.

After applying search with the Hammer category filter, the displayed products should match both the selected category and the search keyword.

#### Actual Result

After selecting the Hammer category checkbox, the page displayed `There are no products found.`

No Hammer-related products were displayed.

The test could not continue to verify search and category filter combination behavior.

#### Notes

The Hammer category filter appears to return no products even though Hammer-related products exist in the default product list.

A separate bug report was created: BUG-001.

This test case is blocked until BUG-001 is fixed.

---

### TC-SEARCH-011: Verify pagination after searching

- Related Scenario: TS-SEARCH-011
- Module: Product Search
- Priority: Medium
- Test Data: Pliers
- Status: Pass

#### Test Steps

1. Open the product listing page.
2. Locate the search input field at the top of the product list.
3. Enter `Pliers` into the search input field.
4. Click the Search button.
5. Observe the search result count.
6. Observe whether pagination is displayed after the search results are loaded.

#### Expected Result

The page should display Pliers-related products.

If the search results fit on one page, pagination should not be displayed.

Pagination should be updated correctly based on the search result count.

#### Actual Result

The page displayed `4 products found for 'Pliers'`.

All displayed products were related to Pliers.

No pagination was displayed after the search results were loaded.

The search results fit on one page.

#### Notes

Pagination was updated correctly after searching.

No unnecessary pagination was displayed when the search result count was small.

No issue found.
