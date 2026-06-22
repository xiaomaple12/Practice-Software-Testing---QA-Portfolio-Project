# Practice Software Testing - QA Portfolio Project

## Project Overview

This is a QA portfolio project based on the Practice Software Testing demo website.

The goal is to demonstrate a complete QA workflow based on the STLC process, including test scenario design, test case writing, manual test execution, regression testing, bug reporting, test summary reporting, SQL validation design, DevTools investigation, and automation scope planning.

Website under test: https://practicesoftwaretesting.com/

## Tested Module

Product Search

## QA Documents Created

* [Test Summary](docs/test-summary.md)
* [Test Scenarios](docs/test-scenarios.md)
* [Test Cases](docs/test-cases.md)
* [Bug Reports](docs/bug-reports.md)
* [SQL Validation Design](docs/sql-validation-design.md)
* [Automation Scope](docs/automation-scope.md)

## DevTools and HTTP Basics

This project also includes Chrome DevTools and HTTP / REST API learning notes.

During testing, Chrome DevTools was used to inspect UI elements, Console errors, Network requests, request methods, status codes, query parameters, request payloads, response bodies, headers, and token-related behavior.

The Network panel was used to compare API responses with UI results. This included verifying whether search keywords were sent correctly, whether requests returned `200 OK`, whether response totals matched the UI, and whether response data contained all expected products.

DevTools evidence was also collected for bug reports, including Console observations, Network request details, status codes, query parameters, response bodies, and initial issue analysis.

Related notes:

* [Chrome DevTools and HTTP / REST API Basics](notes/devtools-http-basics.md)
* [DevTools Bug Report Evidence Notes](notes/bug-report-evidence-notes.md)
* [Test Design Techniques](notes/test-design-techniques.md)
* [Login Decision Table](notes/login-decision-table.md)

## Test Execution Summary

### Cycle 1

| Result Type        | Count |
| ------------------ | ----: |
| Total Scenarios    |    11 |
| Total Test Cases   |    11 |
| Passed             |     8 |
| Failed             |     0 |
| Blocked            |     1 |
| Need Clarification |     2 |
| Open Bugs          |     1 |

### Cycle 2

| Result Type        | Count |
| ------------------ | ----: |
| Total Scenarios    |    12 |
| Total Test Cases   |    13 |
| Passed             |     9 |
| Failed             |     2 |
| Blocked            |     0 |
| Need Clarification |     2 |
| Active Bugs        |     2 |

Cycle 2 preserved the original test-cycle history instead of overwriting Cycle 1 results.

## Key Findings

The following Product Search behaviors remained stable during Cycle 2:

* Full keyword search
* Partial keyword search for common product names
* Non-existing English keyword search
* Reset behavior
* Enter key search
* Case-insensitive search
* Leading and trailing space handling
* Pagination update

The Hammer category filter independently displayed 7 products correctly, including `Sledgehammer`.

However, searching for `Hammer` returned only 6 products and excluded `Sledgehammer`.

The same incomplete result occurred when the Hammer category filter remained selected and `hammer` was entered in the search field.

Chrome DevTools Network evidence confirmed that:

* The request method was `GET`.
* The request URL was `/products/search?q=Hammer`.
* The response status was `200 OK`.
* The response total was 6.
* `Sledgehammer` was not included in the API response.

This indicates that the incomplete result originates from the Search API response rather than the frontend product display.

Two behaviors still require clarification:

* Multiple keyword search
* Localized keyword search

## Bug Reports

### BUG-001

**Hammer category filter returns no products even though Hammer products exist**

* Severity: Medium
* Priority: Medium
* Status: Need Retest
* Related Test Case: TC-SEARCH-010
* Current observation: The issue is intermittent and could not be reproduced consistently during Cycle 2.

### BUG-002

**Search API does not return Sledgehammer when searching for Hammer**

* Severity: Medium
* Priority: Medium
* Status: Open
* Related Test Cases: TC-SEARCH-010 and TC-SEARCH-012
* DevTools finding: The Search API returned `200 OK`, but the response contained only 6 products and excluded `Sledgehammer`.

## SQL Validation Design

This project includes SQL validation design to demonstrate how UI test results could be verified with database queries if database access were available.

Examples include:

* Verifying search result counts from the products table
* Checking partial keyword search results
* Confirming no-result search behavior
* Validating category-to-product relationships
* Investigating whether an issue originates from data, category mapping, API filtering, or frontend behavior

## Automation Scope

The project includes automation scope planning to identify which test cases are suitable for future Playwright automation.

| Automation Candidate    | Count |
| ----------------------- | ----: |
| Suitable for automation |     9 |
| Not recommended yet     |     2 |
| Waiting for bug fix     |     2 |

TC-SEARCH-010 and TC-SEARCH-012 should be manually retested after BUG-002 is fixed before they are added to the automated regression suite.

TC-SEARCH-012 is also suitable for future API response validation because the issue can be verified through both the UI and the Search API response.

## Skills Demonstrated

* STLC-based QA workflow
* Manual test scenario design
* Detailed test case writing
* Manual test execution
* Regression testing
* Historical test-cycle tracking
* Bug reporting
* Intermittent bug handling
* Requirement clarification
* Test summary reporting
* SQL validation thinking
* Automation scope planning
* Chrome DevTools inspection
* HTTP and REST API basics
* API request and response analysis
* UI and API result comparison
* Bug evidence collection with DevTools
* Backend issue identification

## Additional Reference

* [Google Sheets test execution record](https://docs.google.com/spreadsheets/d/1RmrleJbF3qIx1X96Wy92Uo6Qf9AFELIoypBviZyopjo/edit?usp=sharing)
