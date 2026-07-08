# Practice Software Testing - QA Portfolio Project

## Project Overview

This is a QA portfolio project based on the Practice Software Testing demo website.

The goal is to demonstrate a complete QA workflow based on the STLC process, including test scenario design, test case writing, manual test execution, regression testing, bug reporting, test summary reporting, SQL validation design, DevTools investigation, and automation scope planning.

Website under test: https://practicesoftwaretesting.com/

---

## QA Portfolio Project Summary

This project was conducted on the Practice Software Testing website using the official Testing Guide as the primary test basis.

A total of 117 Testing Guide Review records were created, covering major user flows such as registration, login, password management, favorites, invoices, messages, locked account, multi-factor authentication, search, contact form, product listing, category page, product detail page, shopping cart, checkout and payment, geolocation discount, and combined product discount.

### Final Coverage Status

| Coverage Status | Count |
|---|---:|
| Pass | 85 |
| Fail | 7 |
| Need Clarification | 18 |
| Not Testable | 4 |
| Coverage Gap | 3 |
| Total | 117 |

### Bug Report Summary

A total of 7 bug reports were created during the project.

Among them, 4 were selected as portfolio-ready formal bug reports with clearer naming, reproducible steps, issue classification, severity, priority, and supporting observations.

The remaining 3 were early-stage practice bug reports used during the learning and documentation process.

### Portfolio-ready Formal Bug Reports

- BUG-MFA-001: TOTP reuse allowed during the same validity window
- BUG-MFA-002: MFA settings page cannot load existing setup details or provide reset / disable options
- BUG-CONTACT-001: Contact Form validation behavior issue supported by multiple Contact Form review records
- BUG-CAT-001: Category Page filtering behavior issue

### Candidate Issues and Requirement Clarifications

In addition to confirmed failures, the project also documented candidate issues, requirement clarification items, test data gaps, and not-testable scenarios.

Main categories included:

- Registration validation feedback and boundary behavior
- Contact Form testability and requirement mismatch
- Checkout and Payment UX / validation behavior
- Geolocation Discount test data gap
- Discount and invoice validation testability
- Product listing / category navigation state behavior

This helped avoid premature defect classification when the expected behavior, test oracle, account condition, or required test data was unclear.

---

## Tested Modules

This project covered the official Testing Guide modules, including:

- Registration
- Login
- Forgot Password
- Change Password
- Favorites
- Invoices
- Messages
- Locked Account
- Multi-Factor Authentication
- Search
- Contact Form
- Product Listing
- Category Page
- Product Detail Page
- Shopping Cart
- Checkout and Payment
- Geolocation Discount
- Combined Product Discount

---

## QA Documents Created

- Test Summary
- Test Scenarios
- Test Cases
- Bug Reports
- Testing Guide Review
- SQL Validation Design
- Automation Scope
- DevTools API Checklist

---

## DevTools and HTTP Basics

This project also includes Chrome DevTools and HTTP / REST API learning notes.

During testing, Chrome DevTools was used to inspect UI elements, Console errors, Network requests, request methods, status codes, query parameters, request payloads, response bodies, headers, and token-related behavior.

The Network panel was used to compare API responses with UI results. This included verifying whether search keywords were sent correctly, whether requests returned `200 OK`, whether response totals matched the UI, and whether response data contained all expected products.

DevTools evidence was also collected for bug reports, including Console observations, Network request details, status codes, query parameters, response bodies, and initial issue analysis.

Related notes:

- Chrome DevTools and HTTP / REST API Basics
- DevTools Bug Report Evidence Notes
- Test Design Techniques
- Login Decision Table

---

## Test Execution Summary

Earlier test cycles were preserved as part of the project history.

The final Testing Guide Review was later expanded to cover the full official Testing Guide, resulting in 117 review records.

### Final Result

| Coverage Status | Count |
|---|---:|
| Pass | 85 |
| Fail | 7 |
| Need Clarification | 18 |
| Not Testable | 4 |
| Coverage Gap | 3 |
| Total | 117 |

---

## Product Search Key Findings

Product Search was one of the focused test areas in the project.

The following Product Search behaviors remained stable during focused exploratory testing:

- Full keyword search
- Partial keyword search for common product names
- Non-existing English keyword search
- Reset behavior
- Enter key search
- Case-insensitive search
- Leading and trailing space handling
- Pagination update

Case-insensitive testing confirmed that `Hammer`, `hammer`, and `HAMMER` returned the same 6 products.

Search input trimming was also confirmed. A leading space, a trailing space, and spaces on both sides of `Hammer` returned the same results as entering `Hammer` without spaces.

Reset correctly cleared the search field, removed the active search title, and restored the default product list and pagination.

The Hammer category filter independently displayed 7 products correctly, including `Sledgehammer`.

However, searching for `Hammer` returned only 6 products and excluded `Sledgehammer`.

Additional exploratory evidence showed that searching for `ham` returned 7 products and included `Sledgehammer`.

Searching directly for `Sledgehammer` also returned the product successfully.

This result strengthened the early search-related bug report because partial-string matching was supported, but the Search API produced inconsistent results for the related terms `ham` and `Hammer`.

Chrome DevTools Network evidence confirmed that:

- The request method was `GET`.
- The request URL included `/products/search?q=Hammer`.
- The response status was `200 OK`.
- The response total for `q=Hammer` was 6.
- `Sledgehammer` was not included in the `q=Hammer` API response.
- The response for `q=ham` returned 7 products and included `Sledgehammer`.

This indicated that the incomplete result originated from inconsistent Search API matching logic rather than the frontend product display or a general lack of partial-string support.

The following behaviors still required clarification:

- Multiple-keyword search
- Localized keyword search
- Minimum number of characters required to trigger a search

Testing showed that 1-character and 2-character search terms did not trigger a search, while a 3-character term did.

Because the formal requirement was not documented and the UI did not explain the apparent minimum, this finding was recorded as Need Clarification and Coverage Gap rather than a confirmed functional bug.

---

## Bug Reports

A total of 7 bug reports were created during the project.

### Portfolio-ready Formal Bug Reports

- BUG-MFA-001: TOTP reuse allowed during the same validity window
- BUG-MFA-002: MFA settings page cannot load existing setup details or provide reset / disable options
- BUG-CONTACT-001: Contact Form validation behavior issue supported by multiple Contact Form review records
- BUG-CAT-001: Category Page filtering behavior issue

### Early-stage Practice Bug Reports

Early-stage practice bug reports were also preserved as part of the learning and documentation history.

These reports were created earlier in the project to practice bug documentation, retesting, evidence collection, and issue tracking.

---

## SQL Validation Design

This project includes SQL validation design to demonstrate how UI test results could be verified with database queries if database access were available.

Examples include:

- Verifying search result counts from the products table
- Checking partial keyword search results
- Confirming no-result search behavior
- Validating category-to-product relationships
- Investigating whether an issue originates from data, category mapping, API filtering, or frontend behavior

---

## Automation Scope

The project includes automation scope planning to identify which test cases are suitable for future Playwright automation.

| Automation Candidate | Count |
|---|---:|
| Suitable for automation | 8 |
| Not recommended yet | 2 |
| Waiting for bug fix | 2 |

Stable regression candidates include:

- Full keyword search
- Partial keyword search
- Non-existing keyword search
- Reset behavior
- Enter key search
- Case-insensitive search
- Leading and trailing space handling
- Pagination after search

Multiple-keyword search and localized keyword search are not recommended for automation until their expected behavior is clarified.

The minimum search character behavior is also excluded from automation because there is no confirmed requirement or formal test case yet.

Search-related regression test cases should be manually retested after the related bug is fixed before they are added to the automated regression suite.

The current incorrect behavior must not be recorded as the automated expected baseline.

---

## Skills Demonstrated

- STLC-based QA workflow
- Manual test scenario design
- Detailed test case writing
- Manual test execution
- Regression testing
- Historical test-cycle tracking
- Bug reporting
- Intermittent bug handling
- Requirement clarification
- Test summary reporting
- SQL validation thinking
- Automation scope planning
- Chrome DevTools inspection
- HTTP and REST API basics
- API request and response analysis
- UI and API result comparison
- Bug evidence collection with DevTools
- Backend issue identification

---

## Additional Reference

- Google Sheets test execution record
