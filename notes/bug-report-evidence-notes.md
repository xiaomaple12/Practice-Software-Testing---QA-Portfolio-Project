\# DevTools Bug Report Evidence Notes



\## Why DevTools Evidence Matters



When reporting a bug, QA should not only describe what happened on the UI, but also collect evidence from Chrome DevTools.



DevTools evidence helps developers understand whether the issue may be related to frontend behavior, backend API response, request payload, authentication, permission, database handling, or UI rendering.



\---



\## Useful DevTools Areas for Bug Investigation



\### Elements



Elements can be used to inspect UI elements, HTML structure, CSS styles, hidden messages, disabled buttons, and layout issues.



QA can use Elements to check whether an error message exists but is hidden, or whether a button or input field is disabled unexpectedly.



\### Console



Console can be used to check frontend JavaScript errors.



When a bug occurs, QA should check whether any red error appears after the user action.



Useful Console evidence includes:



\* Error message

\* Error type

\* When the error appeared

\* Screenshot of the Console error



If no related error appears, QA should still record:



```text

No related console error was observed.

```



\### Network



Network can be used to inspect API requests and responses.



Useful Network evidence includes:



\* Request URL

\* Request method

\* Status code

\* Query parameters

\* Request payload

\* Response body

\* Authorization header

\* Timing of the request



\---



\## Bug Report Evidence Checklist



A complete bug report can include:



\* Bug title

\* Test environment

\* Precondition

\* Steps to reproduce

\* Expected result

\* Actual result

\* Screenshot or screen recording

\* Console error

\* Network request / response

\* Severity

\* Priority

\* Notes



\---



\## Debugging Logic



If no request is sent after clicking a button, the issue may be related to frontend event handling or request triggering.



If the request payload is incorrect, the issue may be related to frontend request data handling.



If the request payload is correct but the response is incorrect, the issue may be related to backend processing or response data handling.



If the response data is correct but the UI displays incorrect information, the issue may be related to frontend display logic.



If the API returns 401 Unauthorized, the issue may be related to login status, missing token, invalid token, or expired token.



If the API returns 403 Forbidden, the user may be authenticated but does not have permission.



If the API returns 404 Not Found, the requested resource, endpoint, or data may not exist.



If the API returns 500 Internal Server Error, the issue may be related to backend server processing.



\---



\## Practice Scenarios



\### Login failure without error message



If POST /login returns 401 Unauthorized and the response body includes an error message, but the UI does not display the error, the issue may be related to frontend error message display.



\### Search button does not respond



If the user clicks the Search button but no search request appears in the Network panel, the issue may be related to frontend event handling or request triggering.



\### Registration succeeds but database has no new user



If POST /register returns success but SQL verification shows that the user was not added to the users table, the issue may be related to backend data storage or database write handling.



\### Order is created but not displayed in order list



If POST /orders returns success and GET /orders includes the new order, but the UI does not show the order, the issue may be related to frontend list rendering.



\### API returns 500 and UI shows blank page



If GET /products returns 500 Internal Server Error and the UI only shows a blank page, the main issue may be a backend API error. The frontend may also need better error handling or fallback UI.



\---



\## Summary



Through DevTools evidence collection practice, I learned how to provide clearer bug reports by including Console errors, Network request details, status codes, payloads, response bodies, and UI observations.



This helps identify whether an issue may be related to frontend event handling, frontend display logic, backend API processing, database handling, authentication, permission, or server errors.



