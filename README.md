\# Practice Software Testing - QA Portfolio Project



\## Project Overview



This project is a QA portfolio project based on the Practice Software Testing demo website.



The goal of this project is to demonstrate a complete QA workflow using the STLC process, including test scenario design, test case writing, manual test execution, bug reporting, test summary reporting, SQL validation design, and automation scope planning.



Website under test: https://practicesoftwaretesting.com/



\## Tested Module



Product Search



\## QA Documents Created



1\. \[Test Summary](docs/test-summary.md)

2\. \[Test Scenarios](docs/test-scenarios.md)

3\. \[Test Cases](docs/test-cases.md)

4\. \[Bug Reports](docs/bug-reports.md)

5\. \[SQL Validation Design](docs/sql-validation-design.md)

6\. \[Automation Scope](docs/automation-scope.md)



\## Test Execution Summary



For the first test cycle of the Product Search module, 11 test scenarios and 11 test cases were executed.



| Result Type | Count |

|---|---:|

| Passed | 8 |

| Failed | 0 |

| Blocked | 1 |

| Need Clarification | 2 |

| Open Bugs | 1 |



\## Key Findings



The Product Search function worked correctly for the following behaviors:



\- Full keyword search

\- Partial keyword search

\- Non-existing English keyword search

\- Reset behavior

\- Enter key search

\- Case-insensitive search

\- Leading and trailing spaces

\- Pagination update



One issue was found in the Hammer category filter.



The Hammer category filter returned no products even though Hammer-related products existed in the default product list and could be found by searching for `Hammer`.



Two items required clarification because the expected behavior was not clearly defined:



\- Multiple keyword search

\- Localized keyword search



\## Bug Report Example



\*\*BUG-001: Hammer category filter returns no products even though Hammer products exist\*\*



| Field | Details |

|---|---|

| Severity | Medium |

| Priority | Medium |

| Status | Open |

| Related Test Case | TC-SEARCH-010 |



\## SQL Validation Design



This project also includes SQL validation design to show how UI test results could be verified with database queries if database access were available.



Examples include:



\- Verifying search result counts from the products table.

\- Checking partial keyword search results.

\- Confirming no-result search behavior.

\- Investigating whether the Hammer category issue is caused by product data, category mapping, API behavior, or UI filtering logic.



\## Automation Scope



The project includes automation scope planning to identify which test cases are suitable for future Playwright automation.



| Automation Candidate | Count |

|---|---:|

| Suitable for automation | 8 |

| Not recommended yet | 2 |

| Blocked until bug fix | 1 |



\## Skills Demonstrated



\- STLC-based QA workflow

\- Manual test scenario design

\- Test case writing and execution

\- Bug reporting

\- Requirement clarification

\- Test summary reporting

\- SQL validation thinking

\- Automation scope planning

\- Regression testing awareness

