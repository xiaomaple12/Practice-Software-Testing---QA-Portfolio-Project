# Automation Scope

## Purpose

This document defines which Product Search test cases are suitable for future automation.

The goal is not to automate every test case immediately, but to identify stable, repeatable, valuable, and clearly defined cases for future Regression Testing.

## Module

Product Search

## Automation Scope Summary

| Automation Candidate | Count |
| -------------------- | ----: |
| Yes                  |     8 |
| No                   |     2 |
| Blocked              |     2 |
| Total                |    12 |

## Automation Scope List

| Automation ID   | Related Test Case | Automation Candidate | Priority | Suggested Automation Type                           | Reason                                                                                                                                                                                                             |
| --------------- | ----------------- | -------------------- | -------- | --------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| AUTO-SEARCH-001 | TC-SEARCH-001     | Yes                  | High     | UI Automation with Playwright                       | Full keyword search is a stable and important core search function.                                                                                                                                                |
| AUTO-SEARCH-002 | TC-SEARCH-002     | Yes                  | High     | UI Automation with Playwright                       | Partial keyword search is stable for the confirmed keywords `plier` and `ham`. Automation should verify that `plier` returns 4 related products and that `ham` returns 7 products, including `Sledgehammer`.       |
| AUTO-SEARCH-003 | TC-SEARCH-003     | Yes                  | Medium   | UI Automation with Playwright                       | No-result behavior should be verified to ensure users receive clear and consistent feedback when no products match the entered keyword.                                                                            |
| AUTO-SEARCH-004 | TC-SEARCH-004     | Yes                  | High     | UI Automation with Playwright                       | Reset behavior is stable and should verify that the search field is cleared, the active search title is removed, and the default product list and pagination are restored.                                         |
| AUTO-SEARCH-005 | TC-SEARCH-005     | Yes                  | High     | UI Automation with Playwright                       | Enter-key search is an important user interaction and should behave consistently with clicking the Search button.                                                                                                  |
| AUTO-SEARCH-006 | TC-SEARCH-006     | No                   | Low      | Not recommended yet                                 | Multiple-keyword search behavior is not clearly defined. Automation should wait until the expected AND, OR, exact-phrase, or unsupported behavior is confirmed.                                                    |
| AUTO-SEARCH-007 | TC-SEARCH-007     | Yes                  | Medium   | UI Automation with Playwright                       | Case-insensitive search is stable. Automation should verify that `Hammer`, `hammer`, and `HAMMER` return the same result count and the same 6 products.                                                            |
| AUTO-SEARCH-008 | TC-SEARCH-008     | Yes                  | Medium   | UI Automation with Playwright                       | Leading and trailing space handling is stable. Automation should compare a leading space, a trailing space, spaces on both sides, and no extra spaces, and verify that all variations return the same 6 products.  |
| AUTO-SEARCH-009 | TC-SEARCH-009     | No                   | Low      | Not recommended yet                                 | Localized keyword search behavior is not clearly defined, so it should not be automated until the expected requirement is confirmed.                                                                               |
| AUTO-SEARCH-010 | TC-SEARCH-010     | Blocked              | High     | UI Automation with Playwright after bug fix         | The combined search and category-filter test currently fails because searching for `hammer` excludes `Sledgehammer`. Automation should be added only after BUG-002 is fixed and the behavior is manually retested. |
| AUTO-SEARCH-011 | TC-SEARCH-011     | Yes                  | Medium   | UI Automation with Playwright                       | Pagination behavior after searching should be verified because the number of search results determines whether pagination should remain visible.                                                                   |
| AUTO-SEARCH-012 | TC-SEARCH-012     | Blocked              | High     | UI and API validation with Playwright after bug fix | Searching for `Hammer` currently returns only 6 products and excludes `Sledgehammer`, while `ham` returns 7 products and includes it. Automation must wait until BUG-002 is fixed and manually verified.           |

## Recommended Automation Priority

### High Priority

* TC-SEARCH-001: Full keyword search
* TC-SEARCH-002: Partial keyword search using `plier` and `ham`
* TC-SEARCH-004: Reset behavior
* TC-SEARCH-005: Search triggered by pressing Enter

### Medium Priority

* TC-SEARCH-003: No-result behavior
* TC-SEARCH-007: Case-insensitive search
* TC-SEARCH-008: Leading and trailing space handling
* TC-SEARCH-011: Pagination after search

## Stable Automation Candidates

The following cases have clear expected results and produced stable, repeatable outcomes:

* TC-SEARCH-001
* TC-SEARCH-002
* TC-SEARCH-003
* TC-SEARCH-004
* TC-SEARCH-005
* TC-SEARCH-007
* TC-SEARCH-008
* TC-SEARCH-011

These cases are suitable for inclusion in a future Product Search Regression Test Suite.

## Not Recommended Yet

The following test cases should not be automated yet:

* TC-SEARCH-006: Multiple-keyword search
* TC-SEARCH-009: Localized keyword search

The expected behavior for these cases is not clearly defined.

Multiple-keyword search requires clarification of whether the system should use AND logic, OR logic, exact-phrase matching, or reject multiple-keyword input as unsupported.

Localized keyword search requires clarification of whether translated or localized product terms should be supported.

These requirements should be confirmed with the Product Owner, Product Manager, Business Analyst, or requirement documentation before automation is designed.

## Minimum Search Character Coverage

Exploratory Testing showed that 1-character and 2-character keywords did not trigger a search, while a 3-character keyword triggered the search.

The minimum search length is not documented, and the user interface does not provide instructions about the apparent 3-character minimum.

This behavior is currently documented under TS-SEARCH-013 and TGR-SEARCH-001 as Need Clarification and a Coverage Gap.

It should not be added to the automated suite until the expected minimum-character requirement is confirmed.

## Blocked

The following test cases should wait until BUG-002 is fixed:

* TC-SEARCH-010: Search and category-filter combination
* TC-SEARCH-012: Verify that searching for `Hammer` includes `Sledgehammer`

Both tests currently fail because the Search API result for `q=Hammer` does not include `Sledgehammer`.

Additional Exploratory Testing showed that:

* `q=Hammer` returns 6 products and excludes `Sledgehammer`.
* `q=ham` returns 7 products and includes `Sledgehammer`.
* Searching directly for `Sledgehammer` returns the product successfully.

This evidence indicates inconsistent backend search-matching logic.

After BUG-002 is fixed, TC-SEARCH-010 and TC-SEARCH-012 should be manually retested before automation is implemented.

The corrected behavior should not be assumed solely from a successful deployment or a `200 OK` response.

## AUTO-SEARCH-012 Expected Automated Checks

After BUG-002 is fixed and manually verified, AUTO-SEARCH-012 should confirm that:

1. Searching for `Hammer` displays 7 products.
2. `Sledgehammer` is included in the UI results.
3. The GET request for `/products/search?q=Hammer` completes successfully.
4. The API response contains `Sledgehammer`.
5. The API response total matches the number of products displayed in the UI.
6. Related search terms follow the documented and consistent matching rule.

## Key Notes

* Not every manual test case should be automated immediately.
* Stable, repeatable, clearly defined, and high-value regression cases should be automated first.
* Tests with unclear requirements should remain manual until their expected behavior is confirmed.
* Failed tests related to an active bug should be manually retested after the fix before automation is implemented.
* An incorrect result should not be automated as the expected baseline.
* TC-SEARCH-012 is suitable for combined UI and API validation after BUG-002 is fixed.
* The minimum-character behavior should not be automated until its requirement is documented.
