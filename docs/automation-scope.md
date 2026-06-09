# Automation Scope

## Purpose

This document defines which Product Search test cases are suitable for future automation.

The goal is not to automate every test case immediately, but to decide which cases are stable, valuable, and suitable for regression testing.

## Module

Product Search

## Automation Scope Summary

- Yes: 8
- No: 2
- Blocked: 1

## Automation Scope List

### AUTO-SEARCH-001

- Related Test Case: TC-SEARCH-001
- Automation Candidate: Yes
- Priority: High
- Suggested Automation Type: UI Automation with Playwright
- Reason: Full keyword search is a stable and important core search function.

### AUTO-SEARCH-002

- Related Test Case: TC-SEARCH-002
- Automation Candidate: Yes
- Priority: High
- Suggested Automation Type: UI Automation with Playwright
- Reason: Partial keyword search is an important search behavior and should remain stable after future changes.

### AUTO-SEARCH-003

- Related Test Case: TC-SEARCH-003
- Automation Candidate: Yes
- Priority: Medium
- Suggested Automation Type: UI Automation with Playwright
- Reason: No-result behavior should be verified to make sure users receive clear feedback when no products match the keyword.

### AUTO-SEARCH-004

- Related Test Case: TC-SEARCH-004
- Automation Candidate: Yes
- Priority: High
- Suggested Automation Type: UI Automation with Playwright
- Reason: Reset behavior is important because users need a reliable way to clear search results and return to the default product list.

### AUTO-SEARCH-005

- Related Test Case: TC-SEARCH-005
- Automation Candidate: Yes
- Priority: High
- Suggested Automation Type: UI Automation with Playwright
- Reason: Enter key search is an important user interaction and should behave the same as clicking the Search button.

### AUTO-SEARCH-006

- Related Test Case: TC-SEARCH-006
- Automation Candidate: No
- Priority: Low
- Suggested Automation Type: Not recommended yet
- Reason: Multiple keyword search behavior is not clearly defined yet, so it should not be automated until the expected behavior is clarified.

### AUTO-SEARCH-007

- Related Test Case: TC-SEARCH-007
- Automation Candidate: Yes
- Priority: Medium
- Suggested Automation Type: UI Automation with Playwright
- Reason: Case-insensitive search is a common search requirement and should remain stable after future changes.

### AUTO-SEARCH-008

- Related Test Case: TC-SEARCH-008
- Automation Candidate: Yes
- Priority: Medium
- Suggested Automation Type: UI Automation with Playwright
- Reason: Search input trimming is important because users may accidentally enter spaces before or after the keyword.

### AUTO-SEARCH-009

- Related Test Case: TC-SEARCH-009
- Automation Candidate: No
- Priority: Low
- Suggested Automation Type: Not recommended yet
- Reason: Localized keyword search behavior is not clearly defined yet, so it should not be automated until the expected behavior is clarified.

### AUTO-SEARCH-010

- Related Test Case: TC-SEARCH-010
- Automation Candidate: Blocked
- Priority: Medium
- Suggested Automation Type: UI Automation with Playwright after bug fix
- Reason: The test is currently blocked by BUG-001 because the Hammer category filter returns no products.

### AUTO-SEARCH-011

- Related Test Case: TC-SEARCH-011
- Automation Candidate: Yes
- Priority: Medium
- Suggested Automation Type: UI Automation with Playwright
- Reason: Pagination behavior after searching should be verified because search result count affects whether pagination should be displayed.

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
