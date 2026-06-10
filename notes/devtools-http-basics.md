\# Chrome DevTools and HTTP / REST API Basics



\## 1. Chrome DevTools



Chrome DevTools is a browser tool that helps QA inspect what happens behind the UI.



As a QA tester, I can use DevTools to check whether an issue is caused by the UI, JavaScript errors, API request failure, incorrect response data, or network problems.



\## 2. Main DevTools Panels



\### Elements



Elements is used to inspect the HTML structure and CSS styles of a web page.



QA can use it to check whether buttons, input fields, error messages, or hidden elements exist on the page.



\### Console



Console is used to check frontend JavaScript errors.



If a feature does not work and Console shows a red error, the error message can be captured as evidence in a bug report.



\### Network



Network is used to inspect API requests and responses between the frontend and backend.



QA can use Network to check request URL, request method, status code, request payload, response body, headers, and token behavior.



\## 3. HTTP / REST API Basics



\### Request



A request is sent from the frontend to the backend.



Example:



GET /products/search?q=hammer



This means the frontend asks the backend to search for products with the keyword "hammer".



\### Response



A response is returned from the backend to the frontend.



Example:



The backend returns total = 6 and product data for Hammer-related products.



\### HTTP Methods



GET: Retrieve data.



POST: Create or submit data.



PUT: Update data.



DELETE: Delete data.



\## 4. Common Status Codes



200 OK: The request was successful.



400 Bad Request: The request format or data may be invalid.



401 Unauthorized: The user is not authenticated, or the token is missing, invalid, or expired.



403 Forbidden: The user is authenticated but does not have permission.



404 Not Found: The resource or API endpoint was not found.



500 Internal Server Error: The backend server encountered an error.



\## 5. Headers



Headers contain additional information for requests and responses.



Important headers for QA include:



Content-Type: Describes the data format, such as application/json.



Authorization: Usually contains a Bearer token for authenticated requests.



\## 6. Payload / Body



Payload or body is the data sent from the frontend to the backend.



For example, a login request may include email and password.



If the UI shows quantity 3 but the payload sends quantity 1, the issue may be related to frontend request data handling.



\## 7. Token / Bearer Token



A token is like a login pass.



After login, the backend may return a token. The frontend stores it and sends it in later requests.



Example:



Authorization: Bearer <token>



QA can check whether authenticated APIs include the Authorization header.



\## 8. QA Debugging Logic



If no request is sent, the issue may be related to frontend event handling.



If the payload is incorrect, the issue may be related to frontend request data handling.



If the payload is correct but the response is incorrect, the issue may be related to backend processing.



If the response is correct but the UI displays incorrect data, the issue may be related to frontend display logic.



If the status code is 500, the issue may be related to backend server error.



If the status code is 401 or 403, the issue may be related to authentication, token, or permission.



