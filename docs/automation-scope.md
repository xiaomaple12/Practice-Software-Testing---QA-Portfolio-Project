# Automation Scope

## Purpose

This document defines which Product Search test cases are suitable for future automation.

The goal is not to automate every test case immediately, but to decide which cases are stable, valuable, and suitable for regression testing.

## Module

Product Search

## Automation Scope Summary

| Automation Candidate | Count |
| -------------------- | ----: |
| Yes                  |     9 |
| No                   |     2 |
| Blocked              |     2 |

## Automation Scope List

| Automation ID   | Related Test Case | Automation Candidate | Priority | Suggested Automation Type                           | Reason                                                                                                                                                                                        |
| --------------- | ----------------- | -------------------- | -------- | --------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| AUTO-SEARCH-001 | TC-SEARCH-001     | Yes                  | High     | UI Automation with Playwright                       | Full keyword search is a stable and important core search function.                                                                                                                           |
| AUTO-SEARCH-002 | TC-SEARCH-002     | Yes                  | High     | UI Automation with Playwright                       | Partial keyword search is an important search behavior and should remain stable after future changes.                                                                                         |
| AUTO-SEARCH-003 | TC-SEARCH-003     | Yes                  | Medium   | UI Automation with Playwright                       | No-result behavior should be verified to make sure users receive clear feedback when no products match the keyword.                                                                           |
| AUTO-SEARCH-004 | TC-SEARCH-004     | Yes                  | High     | UI Automation with Playwright                       | Reset behavior is important because users need a reliable way to clear search results and return to the default product list.                                                                 |
| AUTO-SEARCH-005 | TC-SEARCH-005     | Yes                  | High     | UI Automation with Playwright                       | Enter key search is an important user interaction and should behave the same as clicking the Search button.                                                                                   |
| AUTO-SEARCH-006 | TC-SEARCH-006     | No                   | Low      | Not recommended yet                                 | Multiple keyword search behavior is not clearly defined, so it should not be automated until the expected behavior is clarified.                                                              |
| AUTO-SEARCH-007 | TC-SEARCH-007     | Yes                  | Medium   | UI Automation with Playwright                       | Case-insensitive search is a common search requirement and should remain stable after future changes.                                                                                         |
| AUTO-SEARCH-008 | TC-SEARCH-008     | Yes                  | Medium   | UI Automation with Playwright                       | Search input trimming is important because users may accidentally enter spaces before or after the keyword.                                                                                   |
| AUTO-SEARCH-009 | TC-SEARCH-009     | No                   | Low      | Not recommended yet                                 | Localized keyword search behavior is not clearly defined, so it should not be automated until the expected behavior is clarified.                                                             |
| AUTO-SEARCH-010 | TC-SEARCH-010     | Blocked              | High     | UI Automation with Playwright after bug fix         | The combined search and category filter test currently fails because searching for `hammer` excludes `Sledgehammer`. Automation should be added after BUG-002 is fixed and manually retested. |
| AUTO-SEARCH-011 | TC-SEARCH-011     | Yes                  | Medium   | UI Automation with Playwright                       | Pagination behavior after searching should be verified because the search result count affects whether pagination should be displayed.                                                        |
| AUTO-SEARCH-012 | TC-SEARCH-012     | Blocked              | High     | UI and API validation with Playwright after bug fix | Searching for `Hammer` currently returns incomplete results and excludes `Sledgehammer`. The test should be automated after BUG-002 is fixed and manually retested.                           |
| AUTO-SEARCH-013 | TC-SEARCH-013     | Yes                  | High     | UI Automation with Playwright                       | The Hammer category filter independently returns a stable and clearly defined result of 7 products, including `Sledgehammer`.                                                                 |

## Recommended Automation Priority

High-priority automation candidates:

* TC-SEARCH-001: Full keyword search
* TC-SEARCH-002: Partial keyword search
* TC-SEARCH-004: Reset behavior
* TC-SEARCH-005: Enter key search
* TC-SEARCH-013: Independent Hammer category filter validation

Medium-priority automation candidates:

* TC-SEARCH-003: No-result behavior
* TC-SEARCH-007: Case-insensitive search
* TC-SEARCH-008: Leading and trailing spaces
* TC-SEARCH-011: Pagination after search

## Not Recommended Yet

The following test cases should not be automated yet:

* TC-SEARCH-006: Multiple keyword search
* TC-SEARCH-009: Localized keyword search

Reason:

The expected behavior is not clearly defined.

These cases should be clarified with PM / PO / BA before automation.

## Blocked

The following test cases should wait until BUG-002 is fixed:

* TC-SEARCH-010: Search and category filter combination
* TC-SEARCH-012: Verify that searching for `Hammer` includes `Sledgehammer`

Reason:

Both tests currently fail because the Search API response for `q=Hammer` does not include `Sledgehammer`.

After BUG-002 is fixed, both cases should be manually retested before being added to the automated regression suite.

## Key Notes

* Not every manual test case should be automated immediately.
* Stable, repeatable, and high-value regression cases should be automated first.
* Tests with unclear requirements should be clarified before automation.
* Failed tests related to an active bug should be manually retested after the fix before automation is implemented.
* TC-SEARCH-012 is suitable for both UI validation and API response validation after BUG-002 is fixed.
