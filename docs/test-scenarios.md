# Test Scenarios

## Project Name

Practice Software Testing - QA Portfolio Project

## Module

Product Search

## Purpose

This document lists the test scenarios designed for the Product Search module.

The goal is to identify what search behaviors should be tested before writing detailed test cases.

## Test Scenario List

### TS-SEARCH-001

- Module: Product Search
- Test Scenario: Verify that users can search products by full product name.
- Priority: High

### TS-SEARCH-002

- Module: Product Search
- Test Scenario: Verify that users can search products by partial keyword.
- Priority: High

### TS-SEARCH-003

- Module: Product Search
- Test Scenario: Verify the system behavior when searching for a non-existing product.
- Priority: Medium

### TS-SEARCH-004

- Module: Product Search
- Test Scenario: Verify that clicking Reset clears the search field and restores the default product list.
- Priority: High

### TS-SEARCH-005

- Module: Product Search
- Test Scenario: Verify whether pressing Enter in the search field triggers the search action.
- Priority: High

### TS-SEARCH-006

- Module: Product Search
- Test Scenario: Verify the system behavior when users enter multiple search keywords.
- Priority: Low

### TS-SEARCH-007

- Module: Product Search
- Test Scenario: Verify that search results are not affected by keyword letter casing.
- Priority: Medium

### TS-SEARCH-008

- Module: Product Search
- Test Scenario: Verify that leading and trailing spaces in the search keyword are handled correctly.
- Priority: Medium

### TS-SEARCH-009

- Module: Product Search
- Test Scenario: Verify the system behavior when searching with localized keywords.
- Priority: Low

### TS-SEARCH-010

- Module: Product Search
- Test Scenario: Verify that search and category filters work together correctly.
- Priority: Medium

### TS-SEARCH-011

- Module: Product Search
- Test Scenario: Verify that pagination is updated correctly after searching.
- Priority: Medium

## Notes

These scenarios cover core search behavior, input handling, filter interaction, and pagination behavior.

Some scenarios require clarification because the expected behavior is not clearly defined.

For example, multiple keyword search and localized keyword search should be confirmed with PM / PO / BA before being treated as pass or fail.
