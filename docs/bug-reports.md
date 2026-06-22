# Bug Reports

## BUG-001: Hammer category filter returns no products even though Hammer products exist

| Field | Details |
|---|---|
| Bug ID | BUG-001 |
| Module | Product Search |
| Severity | Medium |
| Priority | Medium |
| Status | Open |
| Environment | Chrome on Windows, Practice Software Testing demo site |
| Related Test Case | TC-SEARCH-010 |
| Reported By | Kris Hsiao |
| Reported Date | 2026-06-09 |

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

---

## BUG-002: Search API does not return Sledgehammer when searching for Hammer

| Field              | Details                                                            |
| ------------------ | ------------------------------------------------------------------ |
| Bug ID             | BUG-002                                                            |
| Module             | Product Search                                                     |
| Severity           | Medium                                                             |
| Priority           | Medium                                                             |
| Status             | Open                                                               |
| Environment        | Chrome on Windows, Practice Software Testing demo site             |
| Related Test Cases | TC-SEARCH-010, TC-SEARCH-012                                       |
| Reported By        | Kris Hsiao                                                         |
| Reported Date      | 2026-06-22                                                         |
| Request Method     | GET                                                                |
| Request URL        | `https://api.practicesoftwaretesting.com/products/search?q=Hammer` |
| Status Code        | 200 OK                                                             |
| Request Payload    | Query parameter: `q=Hammer`                                        |

## Precondition

User is on the product listing page at https://practicesoftwaretesting.com/.

## Steps to Reproduce

1. Open the product listing page.
2. Under the Hand Tools categories, select the Hammer category checkbox.
3. Verify that 7 products are displayed and that `Sledgehammer` is included.
4. Click Reset to restore the default product list.
5. Open Chrome DevTools and select the Network tab.
6. Enter `Hammer` in the search field.
7. Trigger the search.
8. Select the GET request to `/products/search?q=Hammer`.
9. Inspect the response data and the displayed product list.

## Expected Result

When searching for `Hammer`, the API should return all products whose names contain `hammer`, including `Sledgehammer`.

The UI should display 7 matching products.

## Actual Result

The API returned only 6 products for `q=Hammer`.

`Sledgehammer` was not included in the API response or displayed search results.

Searching directly for `Sledgehammer` returned the product successfully.

## DevTools Evidence

No relevant Console error was observed.

The request was completed successfully with `200 OK`, but the returned data was incomplete.

The response total was 6 and did not include `Sledgehammer`.

## Notes

The Hammer category filter correctly displayed 7 products, including `Sledgehammer`.

The issue appears to be in the backend Search API partial keyword matching logic rather than the frontend display or category filter.

A `200 OK` response confirms that the request was processed successfully, but it does not confirm that the returned product data was correct.
