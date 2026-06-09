# Bug Reports

## BUG-001: Hammer category filter returns no products even though Hammer products exist

- Bug ID: BUG-001
- Module: Product Search
- Severity: Medium
- Priority: Medium
- Status: Open
- Environment: Chrome on Windows, Practice Software Testing demo site
- Related Test Case: TC-SEARCH-010
- Reported By: Kris Hsiao
- Reported Date: 2026-06-09

## Precondition

User is on the product listing page at https://practicesoftwaretesting.com/.

## Steps to Reproduce

1. Open the product listing page.
2. Locate the Filters section on the left side of the page.
3. Under By category, find Hand Tools.
4. Select the Hammer category checkbox.
5. Observe the product list.

## Expected Result

The page should display Hammer-related products after selecting the Hammer category filter.

The displayed products should belong to the Hammer category.

## Actual Result

After selecting the Hammer category checkbox, the page displayed `There are no products found.`

No Hammer-related products were displayed.

## Notes

Hammer-related products exist in the default product list and can be found by searching for `Hammer`.

This suggests that the Hammer category filter may not be returning the expected product list.
