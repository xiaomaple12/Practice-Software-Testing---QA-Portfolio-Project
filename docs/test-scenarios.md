# Test Scenarios

## Project Name

Practice Software Testing - QA Portfolio Project

## Module

Product Search

## Purpose

This document lists the test scenarios designed for the Product Search module.

The goal is to identify what search behaviors should be tested before writing detailed test cases.

## Test Scenario List

| Scenario ID | Module | Test Scenario | Priority |
|---|---|---|---|
| TS-SEARCH-001 | Product Search | Verify that users can search products by full product name. | High |
| TS-SEARCH-002 | Product Search | Verify that users can search products by partial keyword. | High |
| TS-SEARCH-003 | Product Search | Verify the system behavior when searching for a non-existing product. | Medium |
| TS-SEARCH-004 | Product Search | Verify that clicking Reset clears the search field and restores the default product list. | High |
| TS-SEARCH-005 | Product Search | Verify whether pressing Enter in the search field triggers the search action. | High |
| TS-SEARCH-006 | Product Search | Verify the system behavior when users enter multiple search keywords. | Low |
| TS-SEARCH-007 | Product Search | Verify that search results are not affected by keyword letter casing. | Medium |
| TS-SEARCH-008 | Product Search | Verify that leading and trailing spaces in the search keyword are handled correctly. | Medium |
| TS-SEARCH-009 | Product Search | Verify the system behavior when searching with localized keywords. | Low |
| TS-SEARCH-010 | Product Search | Verify that search and category filters work together correctly. | Medium |
| TS-SEARCH-011 | Product Search | Verify that pagination is updated correctly after searching. | Medium |
| TS-SEARCH-012 | Product Search | Verify that the Hammer category filter displays all products belonging to the Hammer category. | High |
## Notes

These scenarios cover core search behavior, input handling, filter interaction, and pagination behavior.

Some scenarios require clarification because the expected behavior is not clearly defined.

For example, multiple keyword search and localized keyword search should be confirmed with PM / PO / BA before being treated as pass or fail.
