# Practice Software Testing - QA Portfolio Project

## Project Overview

This project is a QA portfolio project based on the Practice Software Testing demo website.

The goal of this project is to demonstrate a complete QA workflow using the STLC process, including test scenario design, test case writing, manual test execution, bug reporting, test summary reporting, SQL validation design, and automation scope planning.

Website under test: https://practicesoftwaretesting.com/

## DevTools and HTTP Basics

This project also includes Chrome DevTools and HTTP / REST API learning notes.

During testing, I practiced using Chrome DevTools to inspect UI elements, Console errors, Network requests, request methods, status codes, query parameters, request payloads, response bodies, headers, and token-related behavior.

I also used the Network panel to compare API responses with UI results. For example, when testing product search, I checked whether the search keyword was sent correctly, whether the API returned `200 OK`, whether the response total matched the UI result, and whether no-result behavior was handled correctly.

I also practiced collecting DevTools evidence for bug reports, including Console errors, Network request details, status codes, payloads, response bodies, and initial issue analysis.

Related notes:

* [Chrome DevTools and HTTP / REST API Basics](notes/devtools-http-basics.md)
* [DevTools Bug Report Evidence Notes](notes/bug-report-evidence-notes.md)



## Tested Module

Product Search

## QA Documents Created

- [Test Summary](docs/test-summary.md)
- [Test Scenarios](docs/test-scenarios.md)
- [Test Cases](docs/test-cases.md)
- [Bug Reports](docs/bug-reports.md)
- [SQL Validation Design](docs/sql-validation-design.md)
- [Automation Scope](docs/automation-scope.md)

## Test Execution Summary

For the first test cycle of the Product Search module, 11 test scenarios and 11 test cases were executed.

- Passed: 8
- Failed: 0
- Blocked: 1
- Need Clarification: 2
- Open Bugs: 1

## Key Findings

The Product Search function worked correctly for the following behaviors:

- Full keyword search
- Partial keyword search
- Non-existing English keyword search
- Reset behavior
- Enter key search
- Case-insensitive search
- Leading and trailing spaces
- Pagination update

One issue was found in the Hammer category filter.

The Hammer category filter returned no products even though Hammer-related products existed in the default product list and could be found by searching for `Hammer`.

Two items required clarification because the expected behavior was not clearly defined:

- Multiple keyword search
- Localized keyword search

## Bug Report Example

**BUG-001: Hammer category filter returns no products even though Hammer products exist**

- Severity: Medium
- Priority: Medium
- Status: Open
- Related Test Case: TC-SEARCH-010

## SQL Validation Design

This project also includes SQL validation design to show how UI test results could be verified with database queries if database access were available.

Examples include:

- Verifying search result counts from the products table.
- Checking partial keyword search results.
- Confirming no-result search behavior.
- Investigating whether the Hammer category issue is caused by product data, category mapping, API behavior, or UI filtering logic.

## Automation Scope

The project includes automation scope planning to identify which test cases are suitable for future Playwright automation.

- Suitable for automation: 8
- Not recommended yet: 2
- Blocked until bug fix: 1

## Skills Demonstrated

- STLC-based QA workflow
- Manual test scenario design
- Test case writing and execution
- Bug reporting
- Requirement clarification
- Test summary reporting
- SQL validation thinking
- Automation scope planning
- Regression testing awareness
- Chrome DevTools inspection
- API request and response observation
- Bug evidence collection with DevTools
- Bug report evidence collection with Chrome DevTools

- ## Additional Reference

- Google Sheets test execution record: https://docs.google.com/spreadsheets/d/1RmrleJbF3qIx1X96Wy92Uo6Qf9AFELIoypBviZyopjo/edit?usp=sharing
