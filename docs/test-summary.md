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

- ---

# Test Summary - Cycle 2

## Project Name

Practice Software Testing - QA Portfolio Project

## Module

Product Search

## Test Cycle

Cycle 2

## Tester

Kris Hsiao

## Test Date

2026-06-22

## Test Execution Result

| Result Type        | Count |
| ------------------ | ----: |
| Total Scenarios    |    12 |
| Total Test Cases   |    13 |
| Passed             |     9 |
| Failed             |     2 |
| Blocked            |     0 |
| Need Clarification |     2 |
| Active Bugs        |     2 |

## Test Scope

The second test cycle covered the Product Search module.

The following behaviors were tested:

* Full keyword search
* Partial keyword search
* Non-existing keyword search
* Reset behavior
* Enter key search
* Multiple keyword search
* Case-insensitive search
* Leading and trailing spaces
* Localized keyword search
* Search with category filter
* Pagination after search
* Independent Hammer category filter validation
* Focused validation of whether searching for `Hammer` includes `Sledgehammer`

## Summary

The second test cycle for the Product Search module was completed.

13 test cases were executed across 12 test scenarios.

9 test cases passed.

2 test cases failed.

2 test cases require clarification.

No test cases were blocked.

2 formal bugs remain active.

## Key Findings

Core Product Search behaviors remained stable during Cycle 2.

Full keyword search worked correctly.

Partial keyword search generally worked, but searching for `Hammer` did not return `Sledgehammer`.

Non-existing keyword search worked correctly.

Reset behavior worked correctly.

Pressing Enter triggered the search correctly.

Search behavior remained case-insensitive.

Leading and trailing spaces were handled correctly.

Pagination was updated correctly after searching.

The Hammer category filter independently displayed 7 products, including `Sledgehammer`.

When the Hammer category filter remained selected and `hammer` was searched, only 6 products were displayed.

Searching for `Hammer` without a category filter also returned only 6 products and excluded `Sledgehammer`.

DevTools Network evidence confirmed that the Search API response itself did not include `Sledgehammer`.

## Failed Test Cases

* TC-SEARCH-010: Search and category filter combination returned incomplete results.
* TC-SEARCH-012: Searching for `Hammer` did not include `Sledgehammer`.

Both failures are related to BUG-002.

## Risks / Clarifications

The expected behavior for multiple keyword search remains undefined.

Need to clarify whether multiple keyword search should use AND logic, OR logic, exact phrase matching, or unsupported behavior.

The expected behavior for localized keyword search remains undefined.

Need to clarify whether localized keyword search should be supported.

BUG-001 is intermittent and could not be reproduced consistently during retesting.

BUG-001 remains in `Need Retest` status.

BUG-002 remains `Open` because the Search API returns incomplete results for the keyword `Hammer`.

## Next Steps

Clarify the expected behavior for multiple keyword search with PM / PO / BA.

Clarify the expected behavior for localized keyword search with PM / PO / BA.

Continue monitoring and retesting BUG-001.

Retest TC-SEARCH-010 and TC-SEARCH-012 after BUG-002 is fixed.

Update the remaining GitHub portfolio documentation with Cycle 2 results.

## Portfolio Notes

Cycle 2 demonstrates regression test execution and historical test-cycle tracking.

It shows how an intermittent issue can remain under observation when it cannot be reproduced consistently.

It includes DevTools Network investigation and identifies that an incomplete search result originates from the backend Search API response.

It also demonstrates how new focused test coverage was added after discovering a defect.

