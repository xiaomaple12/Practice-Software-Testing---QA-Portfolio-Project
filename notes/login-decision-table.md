 # Login Decision Table



This document records the decision table and related test cases for the login function in the QA Side Project.



 ## Conditions



 * The account is correct.

 * The password is correct.

 * The account is locked.



 ## Actions



 * Login succeeds and the user enters the member page.

 * Login fails and an account or password error message is displayed.

 * Login fails and an account locked message is displayed.



 ## Decision Table



`-` means  * *Don't Care * *. The condition does not affect the result for that rule.



| Condition / Action             | Rule 1 | Rule 2 | Rule 3 | Rule 4 |

| ------------------------------ | ------ | ------ | ------ | ------ |

| Account is correct             | Yes    | Yes    | Yes    | No     |

| Password is correct            | Yes    | No     | -      | -      |

| Account is locked              | No     | No     | Yes    | -      |

| Login succeeds                 | Yes    | No     | No     | No     |

| Show account or password error | No     | Yes    | No     | Yes    |

| Show account locked message    | No     | No     | Yes    | No     |



 ## Test Cases Derived from the Decision Table



 ### TC-LOGIN-DT-001 — Valid Account and Password



 * *Test Data * *



 * Account: `admin@gmail.com`

 * Password: `admin123`

 * Account Status: `Unlocked`



 * *Expected Result * *



 * Login succeeds.

 * The user enters the member page.



 ### TC-LOGIN-DT-002 — Valid Account with Incorrect Password



 * *Test Data * *



 * Account: `admin@gmail.com`

 * Password: `wrongpassword`

 * Account Status: `Unlocked`



 * *Expected Result * *



 * Login fails.

 * The system displays an account or password error message.



 ### TC-LOGIN-DT-003 — Locked Account with Correct Password



 * *Test Data * *



 * Account: `lockeduser@gmail.com`

 * Password: `locked123`

 * Account Status: `Locked`



 * *Expected Result * *



 * Login fails.

 * The system displays an account locked message.



 ### TC-LOGIN-DT-004 — Invalid Account and Password



 * *Test Data * *



 * Account: `invalid@gmail.com`

 * Password: `wrongpassword`

 * Account Status: `Unlocked`



 * *Expected Result * *



 * Login fails.

 * The system displays an account or password error message.





