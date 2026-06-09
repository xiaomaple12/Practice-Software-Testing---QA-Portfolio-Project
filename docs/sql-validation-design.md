# SQL Validation Design

## Purpose

This document describes how SQL queries could be used to validate Product Search test results if database access were available.

The goal is not to directly connect to the demo site's database, but to demonstrate how QA can use SQL to verify UI results, search result counts, product data, and possible data-related causes of bugs.

## Module

Product Search

## SQL Validation List

| Validation ID | Related Test Case | Validation Purpose | Example SQL Query | Expected Database Result |
|---|---|---|---|---|
| SQL-VAL-SEARCH-001 | TC-SEARCH-001 | Verify that full product name search results match product data in the database. | `SELECT * FROM products WHERE name LIKE '%Pliers%';` | The query should return 4 product records related to Pliers. |
| SQL-VAL-SEARCH-002 | TC-SEARCH-002 | Verify that partial keyword search results match product data in the database. | `SELECT * FROM products WHERE LOWER(name) LIKE '%plier%';` | The query should return the same 4 product records as the full keyword search. |
| SQL-VAL-SEARCH-003 | TC-SEARCH-003 | Verify that a non-existing keyword does not match any product records in the database. | `SELECT * FROM products WHERE name LIKE '%abcdefg12345%';` | The query should return 0 product records. |
| SQL-VAL-SEARCH-004 | TC-SEARCH-004 | Verify that reset behavior restores the default product listing data. | `SELECT * FROM products ORDER BY id ASC;` | The query should return the default product records in the expected order. |
| SQL-VAL-SEARCH-005 | TC-SEARCH-005 | Verify that pressing Enter triggers the same search result as clicking the Search button. | `SELECT * FROM products WHERE name LIKE '%Hammer%';` | The query should return 6 Hammer-related product records. |
| SQL-VAL-SEARCH-006 | TC-SEARCH-007 | Verify that search results are case-insensitive. | `SELECT * FROM products WHERE LOWER(name) LIKE '%hammer%';` | The query should return the same 6 Hammer-related product records as searching for "Hammer". |
| SQL-VAL-SEARCH-007 | TC-SEARCH-008 | Verify that leading and trailing spaces do not affect product search results. | `SELECT * FROM products WHERE LOWER(name) LIKE '%hammer%';` | The query should return the same 6 Hammer-related product records as searching for "hammer" without spaces. |
| SQL-VAL-SEARCH-008 | TC-SEARCH-010 | Verify whether Hammer category has product records in the database. | `SELECT p.* FROM products p JOIN categories c ON p.category_id = c.id WHERE c.name = 'Hammer';` | The query should return Hammer-related product records if the Hammer category is correctly linked to products. |
| SQL-VAL-SEARCH-009 | TC-SEARCH-011 | Verify that pagination is not needed when search result count fits on one page. | `SELECT COUNT(*) FROM products WHERE name LIKE '%Pliers%';` | The query should return 4. Since the result count is small, pagination should not be displayed. |

## Key Notes

- SQL validation can help compare UI results with database records.
- SQL validation can be used to verify search result counts.
- SQL validation can help confirm whether no-result behavior is consistent with product data.
- SQL validation can support bug investigation by checking whether an issue may come from data, category mapping, API filtering, or UI behavior.

## Bug Investigation Example

For BUG-001, the Hammer category filter returned no products on the UI even though Hammer-related products existed in the product list.

If database access were available, SQL validation could help check whether Hammer products are correctly linked to the Hammer category.

This would help narrow down whether the issue is caused by missing category-product data, incorrect category mapping, API behavior, or UI filter behavior.
