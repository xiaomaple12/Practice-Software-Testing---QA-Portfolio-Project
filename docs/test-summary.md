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

| Result Type        | Count |
| ------------------ | ----: |
| Total Scenarios    |    11 |
| Total Test Cases   |    11 |
| Passed             |     8 |
| Failed             |     0 |
| Blocked            |     1 |
| Need Clarification |     2 |
| Open Bugs          |     1 |

## Test Scope

The first test cycle covered the Product Search module.

The following search behaviors were tested:

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

* Clarify expected behavior for multiple keyword search with PM / PO / BA.
* Clarify expected behavior for localized keyword search with PM / PO / BA.
* Retest TC-SEARCH-010 after BUG-001 is fixed.
* Continue building Bug Reports, SQL Validation Design, Automation Scope, and Test Summary documentation.

---

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

2026-06-29

## Test Execution Result

| Result Type        | Count |
| ------------------ | ----: |
| Total Scenarios    |    13 |
| Total Test Cases   |    13 |
| Passed             |     9 |
| Failed             |     2 |
| Blocked            |     0 |
| Need Clarification |     2 |
| Active Bugs        |     2 |

## Test Scope

The second test cycle covered the Product Search module and was later supplemented with focused Exploratory Testing.

The following behaviors were tested:

* Full keyword search
* Partial keyword search
* Non-existing keyword search
* Reset behavior
* Enter key search
* Multiple-keyword search
* Case-insensitive search
* Leading and trailing spaces
* Localized keyword search
* Search with category filter
* Pagination after search
* Independent Hammer category filter validation
* Focused validation of whether searching for `Hammer` includes `Sledgehammer`
* Minimum search character exploratory review

## Summary

The second test cycle for the Product Search module was completed and later supplemented with focused Exploratory Testing.

13 test cases were executed across 13 test scenarios.

9 test cases passed.

2 test cases failed.

2 test cases require clarification.

No test cases were blocked.

2 formal bugs remain active.

The exploratory session added one documented coverage gap for the minimum number of characters required to trigger a search.

## Key Findings

Core Product Search behaviors remained stable during Cycle 2 and focused Exploratory Testing.

Full keyword search worked correctly.

Partial keyword search worked for the tested keywords `plier` and `ham`.

Searching for `plier` returned 4 related products.

Searching for `ham` returned 7 products and included `Sledgehammer`.

Searching for `Hammer` returned only 6 products and excluded `Sledgehammer`.

Searching directly for `Sledgehammer` returned the product successfully.

This additional evidence strengthens BUG-002 because partial-string matching is supported, but the related search terms `ham` and `Hammer` produce inconsistent results.

Chrome DevTools Network evidence confirmed that the request for `q=Hammer` returned `200 OK`, but the API response contained only 6 products and excluded `Sledgehammer`.

The response for `q=ham` returned 7 products and included `Sledgehammer`.

This suggests that the incomplete result originates from inconsistent backend search matching logic rather than the frontend display or a general lack of partial-string support.

Case-insensitive search was confirmed using `Hammer`, `hammer`, and `HAMMER`.

All three letter-case variations returned the same 6 products.

Leading and trailing spaces were handled correctly.

A leading space, a trailing space, and spaces on both sides of `Hammer` returned the same result count and product list as `Hammer` without spaces.

Reset cleared the search field, removed the active search title, and restored the default product list and pagination.

Pagination was updated correctly after searching.

The Hammer category filter independently displayed 7 products, including `Sledgehammer`.

## Failed Test Cases

* TC-SEARCH-010: Search and category filter combination returned incomplete results.
* TC-SEARCH-012: Searching for `Hammer` did not include `Sledgehammer`.

Both failed test cases are related to BUG-002.

## Risks / Clarifications

The expected behavior for multiple-keyword search remains undefined.

The requirement does not confirm whether multiple keywords should use AND logic, OR logic, exact-phrase matching, or be unsupported.

If multiple-keyword search is unsupported, the user interface may need to provide clear guidance or a validation message.

The expected behavior for localized keyword search remains undefined.

The requirement does not confirm whether localized keyword search should be supported.

The minimum number of characters required to trigger a search is not documented.

Testing showed that a 1-character keyword and a 2-character keyword did not trigger a search, while a 3-character keyword triggered the search.

The user interface does not explain the apparent 3-character minimum.

This behavior is recorded as Need Clarification and a Coverage Gap rather than a Functional Bug because the expected requirement has not been confirmed.

BUG-001 is intermittent and could not be reproduced consistently during retesting.

BUG-001 remains in `Need Retest` status.

BUG-002 remains `Open` because the Search API produces incomplete and inconsistent results for the keyword `Hammer`.

## Next Steps

* Clarify the intended multiple-keyword search behavior with the Product Owner, Business Analyst, or requirement documentation.
* Clarify whether localized keyword search should be supported.
* Clarify the minimum number of characters required to trigger a product search.
* Confirm whether the user interface should display instructions or validation when the entered keyword is shorter than the required minimum.
* Continue monitoring and retesting BUG-001.
* Retest TC-SEARCH-010 and TC-SEARCH-012 after BUG-002 is fixed.
* Manually confirm the corrected `Hammer` search behavior before adding AUTO-SEARCH-012 to the automated regression suite.
* Keep partial keyword search, case-insensitive search, leading and trailing space handling, Reset behavior, and pagination in the future regression scope.
* Do not automate multiple-keyword search, localized keyword search, or the minimum-character rule until their expected requirements are confirmed.

## Portfolio Notes

Cycle 2 demonstrates structured regression execution, focused Exploratory Testing, and historical test-cycle tracking.

It shows how exploratory findings were compared with existing Test Scenarios, Test Cases, Bug Reports, Testing Guide Review, Test Summary, and Automation Scope before new documentation was added.

It demonstrates reuse and expansion of existing test coverage instead of creating duplicate Test Cases.

It strengthens BUG-002 with UI and API evidence comparing the search terms `ham` and `Hammer`.

It demonstrates how an intermittent issue can remain under observation when it cannot be reproduced consistently.

It includes requirement clarification handling for multiple-keyword search, localized keyword search, and the minimum search character rule.

It demonstrates boundary-value thinking, partial-string testing, regression planning, Chrome DevTools investigation, API response analysis, and automation candidate evaluation.

It also shows that stable behaviors were selected for future automation, while undefined behaviors and known defects were excluded or marked as waiting for clarification or bug resolution.
