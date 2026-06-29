# Bug Reports

## BUG-001: Hammer category filter returns no products even though Hammer products exist

| Field             | Details                                                |
| ----------------- | ------------------------------------------------------ |
| Bug ID            | BUG-001                                                |
| Module            | Product Search                                         |
| Severity          | Medium                                                 |
| Priority          | Medium                                                 |
| Status            | Open                                                   |
| Environment       | Chrome on Windows, Practice Software Testing demo site |
| Related Test Case | TC-SEARCH-010                                          |
| Reported By       | Kris Hsiao                                             |
| Reported Date     | 2026-06-09                                             |

## Precondition

User is on the product listing page at https://practicesoftwaretesting.com/.

## Steps to Reproduce

1. Open the Practice Software Testing product listing page.
2. Locate the Filters section on the left side of the page.
3. Locate the By category section.
4. Expand Hand Tools if the category list is collapsed.
5. Select the Hammer category checkbox.
6. Wait for the filtered product list to load.
7. Observe the displayed product count and product cards.

## Expected Result

The page should display Hammer-related products after selecting the Hammer category filter.

The displayed products should belong to the Hammer category.

## Actual Result

After selecting the Hammer category checkbox, the page displayed `There are no products found.`

No Hammer-related products were displayed.

## Notes

Hammer-related products exist in the default product list and can be found by searching for `Hammer`.

This suggests that the Hammer category filter may not be returning the expected product list.

---

## BUG-002: Search API does not return Sledgehammer when searching for Hammer

| Field              | Details                                                                                                                                |
| ------------------ | -------------------------------------------------------------------------------------------------------------------------------------- |
| Bug ID             | BUG-002                                                                                                                                |
| Module             | Product Search                                                                                                                         |
| Severity           | Medium                                                                                                                                 |
| Priority           | Medium                                                                                                                                 |
| Status             | Open                                                                                                                                   |
| Environment        | Chrome on Windows, Practice Software Testing demo site                                                                                 |
| Related Test Cases | TC-SEARCH-010, TC-SEARCH-012                                                                                                           |
| Reported By        | Kris Hsiao                                                                                                                             |
| Reported Date      | 2026-06-22                                                                                                                             |
| Request Method     | GET                                                                                                                                    |
| Request URLs       | `https://api.practicesoftwaretesting.com/products/search?q=Hammer` and `https://api.practicesoftwaretesting.com/products/search?q=ham` |
| Status Code        | 200 OK                                                                                                                                 |
| Request Payload    | N/A. The GET requests used the query parameters `q=Hammer` and `q=ham`.                                                                |

## Precondition

The user is on the Practice Software Testing product listing page.

No category filter is selected.

Chrome DevTools is available for Network request inspection.

## Steps to Reproduce

1. Open the Practice Software Testing product listing page.
2. Confirm that no category filter is currently selected.
3. Locate the Search section on the left side of the product listing page.
4. Click the search input field.
5. Enter `Hammer`.
6. Click the Search button.
7. Wait for the search results to load.
8. Record the displayed result count.
9. Record the names of all displayed products.
10. Verify whether `Sledgehammer` is included in the displayed results.
11. Open Chrome DevTools by pressing F12.
12. Select the Network tab.
13. Repeat the search for `Hammer`.
14. Locate and select the GET request to `/products/search?q=Hammer`.
15. Open the Response section for the selected request.
16. Record the response total and verify whether the returned product data includes `Sledgehammer`.
17. Return to the product listing page.
18. Click Reset to clear the active search and restore the default product list.
19. Enter `ham` into the search input field.
20. Click the Search button.
21. Wait for the search results to load.
22. Record the displayed result count.
23. Verify whether `Sledgehammer` is included in the displayed results.
24. Return to the Network tab in Chrome DevTools.
25. Locate and select the GET request to `/products/search?q=ham`.
26. Open the Response section for the selected request.
27. Record the response total and verify whether the returned product data includes `Sledgehammer`.
28. Compare the UI results and API responses from the `Hammer` and `ham` searches.
29. Reset the search again.
30. Search directly for `Sledgehammer`.
31. Verify that the product can be found when its full name is entered.

## Expected Result

Searching for `Hammer` should return all products whose names contain the matching search text, including `Sledgehammer`.

The UI should display 7 matching products.

The Search API response for `q=Hammer` should contain `Sledgehammer`.

Searching for the related partial keyword `ham` should follow the same documented search-matching rule and return consistent results.

## Actual Result

Searching for `Hammer` returned only 6 products.

`Sledgehammer` was excluded from both the Search API response and the displayed UI results.

Searching for `ham` returned 7 products and included `Sledgehammer`.

Searching directly for `Sledgehammer` also returned the product successfully.

The search results were inconsistent because the shorter partial string `ham` found `Sledgehammer`, while the related and more specific search term `Hammer` did not.

## Additional Investigation

The Hammer category filter independently displayed 7 products, including `Sledgehammer`.

This confirms that the product exists in the available data and can be displayed correctly by the frontend.

The successful `ham` search confirms that partial-string matching is supported.

Therefore, the issue is more likely caused by inconsistent backend search-matching logic than by a general lack of partial-string support.

The issue does not appear to originate from the frontend product display because the UI accurately reflects the products returned by each API response.

## DevTools Evidence

No relevant Console error was observed.

Both Search API requests completed successfully with `200 OK`.

The response for `q=Hammer` returned a total of 6 products and did not include `Sledgehammer`.

The response for `q=ham` returned a total of 7 products and included `Sledgehammer`.

A successful HTTP status confirms that each request was processed, but it does not confirm that the returned product data was logically complete or consistent.

## Response Body Comparison

### Request: `q=Hammer`

The response returned a total of 6 products.

`Sledgehammer` was not included in the returned product data.

### Request: `q=ham`

The response returned a total of 7 products.

`Sledgehammer` was included in the returned product data.

## Evidence

DevTools Network evidence was captured for the following searches:

* `q=Hammer`
* `q=ham`
* `q=Sledgehammer`

Searching for `ham` returned 7 products, including `Sledgehammer`.

Searching for `Hammer` returned only 6 products and excluded `Sledgehammer`.

Searching directly for `Sledgehammer` returned the product successfully.

## Notes

Additional Exploratory Testing strengthened the original bug evidence.

The new result confirms that the system supports partial-string searching because `ham` successfully returns `Sledgehammer`.

The issue should therefore be treated as an inconsistency in the Search API matching logic rather than a simple limitation where partial keywords are unsupported.

Related test cases:

* TC-SEARCH-010
* TC-SEARCH-012

BUG-002 should remain Open until the Search API returns consistent and complete results for related search terms.

After the bug is fixed, TC-SEARCH-010 and TC-SEARCH-012 should be manually retested before AUTO-SEARCH-012 is added to the automated regression suite.
