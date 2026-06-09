# Test Summary

## Project Name

Practice Software Testing - QA Portfolio Project

## Module

Product Search

## Test Cycle

Cycle 1

## Tester

Kris Hsiao

## Test Date

2026-06-09

## Test Execution Result

| Result Type | Count |
|---|---:|
| Total Scenarios | 11 |
| Total Test Cases | 11 |
| Passed | 8 |
| Failed | 0 |
| Blocked | 1 |
| Need Clarification | 2 |
| Open Bugs | 1 |

## Test Scope

The first test cycle covered the Product Search module.

The following search behaviors were tested:

- Full keyword search
- Partial keyword search
- Non-existing keyword search
- Reset behavior
- Enter key search
- Multiple keyword search
- Case-insensitive search
- Leading and trailing spaces
- Localized keyword search
- Search with category filter
- Pagination after search

## Summary

The first test cycle for the Product Search module was completed.

11 test scenarios and 11 test cases were executed.

8 test cases passed.

2 test cases require clarification.

1 test case was blocked due to a category filter issue.

1 open bug was reported.

## Key Findings

Product search works correctly for full keyword search.

Product search works correctly for partial keyword search.

Product search handles non-existing English keywords correctly.

Reset behavior works as expected.

Pressing Enter triggers the search action.

Search behavior appears case-insensitive.

Leading and trailing spaces are trimmed correctly.

Pagination is updated correctly after searching.

The Hammer category filter returned no products even though Hammer-related products exist.

Localized keyword search behavior requires clarification.

Multiple keyword search behavior requires clarification.

## Risks / Clarifications

The expected behavior for multiple keyword search is not clearly defined.

Need to clarify whether multiple keyword search should use AND, OR, exact phrase, or unsupported behavior.

The expected behavior for localized keyword search is not clearly defined.

Need to clarify whether localized keyword search should be supported.

The Hammer category filter issue blocks validation of combined search and category filter behavior.

## Next Steps

- Clarify expected behavior for multiple keyword search with PM / PO / BA.
- Clarify expected behavior for localized keyword search with PM / PO / BA.
- Retest TC-SEARCH-010 after BUG-001 is fixed.
- Continue building Bug Reports, SQL Validation Design, Automation Scope, and Test Summary documentation.
