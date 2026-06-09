# Automation Scope

## Purpose

This document defines which Product Search test cases are suitable for future automation.

The goal is not to automate every test case immediately, but to decide which cases are stable, valuable, and suitable for regression testing.

## Module

Product Search

### Automation Scope Summary

| Automation Candidate | Count |
|---|---:|
| Yes | 8 |
| No | 2 |
| Blocked | 1 |

## Automation Scope List

| Automation ID | Related Test Case | Automation Candidate | Priority | Suggested Automation Type | Reason |
|---|---|---|---|---|---|
| AUTO-SEARCH-001 | TC-SEARCH-001 | Yes | High | UI Automation with Playwright | Full keyword search is a stable and important core search function. |
| AUTO-SEARCH-002 | TC-SEARCH-002 | Yes | High | UI Automation with Playwright | Partial keyword search is an important search behavior and should remain stable after future changes. |
| AUTO-SEARCH-003 | TC-SEARCH-003 | Yes | Medium | UI Automation with Playwright | No-result behavior should be verified to make sure users receive clear feedback when no products match the keyword. |
| AUTO-SEARCH-004 | TC-SEARCH-004 | Yes | High | UI Automation with Playwright | Reset behavior is important because users need a reliable way to clear search results and return to the default product list. |
| AUTO-SEARCH-005 | TC-SEARCH-005 | Yes | High | UI Automation with Playwright | Enter key search is an important user interaction and should behave the same as clicking the Search button. |
| AUTO-SEARCH-006 | TC-SEARCH-006 | No | Low | Not recommended yet | Multiple keyword search behavior is not clearly defined yet, so it should not be automated until the expected behavior is clarified. |
| AUTO-SEARCH-007 | TC-SEARCH-007 | Yes | Medium | UI Automation with Playwright | Case-insensitive search is a common search requirement and should remain stable after future changes. |
| AUTO-SEARCH-008 | TC-SEARCH-008 | Yes | Medium | UI Automation with Playwright | Search input trimming is important because users may accidentally enter spaces before or after the keyword. |
| AUTO-SEARCH-009 | TC-SEARCH-009 | No | Low | Not recommended yet | Localized keyword search behavior is not clearly defined yet, so it should not be automated until the expected behavior is clarified. |
| AUTO-SEARCH-010 | TC-SEARCH-010 | Blocked | Medium | UI Automation with Playwright after bug fix | The test is currently blocked by BUG-001 because the Hammer category filter returns no products. |
| AUTO-SEARCH-011 | TC-SEARCH-011 | Yes | Medium | UI Automation with Playwright | Pagination behavior after searching should be verified because search result count affects whether pagination should be displayed. |

## Recommended Automation Priority

High priority automation candidates:

- TC-SEARCH-001: Full keyword search
- TC-SEARCH-002: Partial keyword search
- TC-SEARCH-004: Reset behavior
- TC-SEARCH-005: Enter key search

Medium priority automation candidates:

- TC-SEARCH-003: No-result behavior
- TC-SEARCH-007: Case-insensitive search
- TC-SEARCH-008: Leading and trailing spaces
- TC-SEARCH-011: Pagination after search

## Not Recommended Yet

The following test cases should not be automated yet:

- TC-SEARCH-006: Multiple keyword search
- TC-SEARCH-009: Localized keyword search

Reason: The expected behavior is not clearly defined yet. These cases should be clarified with PM / PO / BA before automation.

## Blocked

The following test case is blocked:

- TC-SEARCH-010: Search and category filter combination

Reason: This test is blocked by BUG-001. The Hammer category filter currently returns no products, so the combined search and category filter behavior cannot be verified.

## Key Notes

- Not every manual test case should be automated immediately.
- Stable, repeatable, and high-value regression cases should be automated first.
- Tests with unclear requirements should be clarified before automation.
- Blocked tests should be retested manually after the related bug is fixed before being added to the automation scope.
