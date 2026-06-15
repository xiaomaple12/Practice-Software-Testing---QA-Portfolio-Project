 # Test Design Techniques



This document records practical examples of Smoke Testing, Sanity Testing, Regression Testing, Equivalence Partitioning, and Boundary Value Analysis for an e-commerce QA side project.



 ## 1. Smoke Test Checklist



The purpose of Smoke Testing is to quickly confirm that the main business flow is working before starting detailed testing.



 *  [ ] Log in with a valid account and confirm the user enters the member page successfully.

 *  [ ] Open the product listing page and confirm product names, images, and prices are displayed correctly.

 *  [ ] Search for `Hammer` and confirm related products appear in the product list.

 *  [ ] Add a Hammer product to the cart and confirm the success message appears and the product is displayed in the cart.

 *  [ ] Complete checkout using valid billing information and `Cash on Delivery`, then confirm the system displays `Payment was successful` and an order number.

## 2. Sanity Test Examples

Sanity Testing focuses on the specific function that was recently fixed or changed.

### Product Quantity Fix

Bug fix: The system previously allowed users to enter a quantity greater than 99.

Quick verification data:

* `99` → should be accepted.
* `100` → should be rejected.
* `101` → should be rejected.

### Product Search Fix

Bug fix: Searching for `Hammer` previously returned no results.

Quick verification data:

* `Hammer`
* `hammer`
* `hammer `

The search should return relevant products for all supported input variations.

### Order Number Fix

Bug fix: The order number was not displayed after successful payment.

Verify that:

* The page displays `Payment was successful`.
* A valid order number is displayed.

## 3. Regression Test Examples

Regression Testing confirms that a recent change has not broken other related functions.

### After Product Search Changes

Verify that:

* Reset clears the search condition and restores the full product list.
* Pagination displays the correct number of pages.
* Search can still work together with category filters.
* Product detail pages can still be opened from the search results.

### After Login Changes

Verify that:

* Products previously added to the cart are still displayed after login.
* The user remains logged in during checkout.
* Logging out prevents access to member-only pages and order history.

### After Cart Changes

Verify that:

* `Continue Shopping` returns the user to the product page.
* Product quantity can still be updated.
* Product totals and order totals update correctly.
* The user can still proceed from the cart to checkout.

### After Payment or Order Changes

Verify that:

* Payment or transaction status is recorded correctly.
* The new order appears in the user's order history.
* Order details and order status are correct.
* The cart is cleared after the order is completed.

## 4. Password Equivalence Partitioning

Requirement: Password length must be between 8 and 20 characters.

| Partition               | Type    | Test Data               | Expected Result                                                                                                 |
| ----------------------- | ------- | ----------------------- | --------------------------------------------------------------------------------------------------------------- |
| Empty input             | Invalid | `<empty>`               | The system rejects the input and displays a required-field message.                                             |
| 1–7 characters          | Invalid | `asd`                   | The system rejects the password and displays a message that at least 8 characters are required.                 |
| 8–20 characters         | Valid   | `rottweiler`            | The system accepts the password, displays no length error, and allows the user to continue submitting the form. |
| More than 20 characters | Invalid | `xiaomaplerottweiler12` | The system rejects the password and displays a message that the maximum length is 20 characters.                |

## 5. Product Quantity Boundary Value Analysis

Requirement: Product quantity must be between 1 and 99.

| Test Data | Boundary Position      | Expected Result                                                                         |
| --------- | ---------------------- | --------------------------------------------------------------------------------------- |
| `0`       | Just below the minimum | The system rejects the quantity and displays a message that the minimum quantity is 1.  |
| `1`       | Minimum valid value    | The system accepts the quantity and displays 1 item in the cart.                        |
| `2`       | Just above the minimum | The system accepts the quantity and displays 2 items in the cart.                       |
| `98`      | Just below the maximum | The system accepts the quantity and displays 98 items in the cart.                      |
| `99`      | Maximum valid value    | The system accepts the quantity and displays 99 items in the cart.                      |
| `100`     | Just above the maximum | The system rejects the quantity and displays a message that the maximum quantity is 99. |

When a valid quantity is accepted, the product total should equal:

`Unit Price × Quantity`



