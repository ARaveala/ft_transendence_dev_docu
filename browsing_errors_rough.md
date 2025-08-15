Not handling all possible outcomes:
The project's requirements state there should be no unhandled errors. This means your code needs to be defensive.
A common beginner mistake is to assume a function will always return a valid result. For example, a function that reads from a file
might fail because the file doesn't exist, and a function that fetches data from a server might fail because the network is down.

Your code should include mechanisms to handle these potential failures gracefully.
Here are some common types of runtime errors to be aware of and how to handle them:

- API Calls & Network Issues: A network request can fail for many reasons (e.g., server is down, no internet connection, invalid URL). Your code should always use try/catch blocks with async/await to handle these and check for HTTP error status codes.
- File System Errors: When your backend is reading or writing files, you must handle potential errors like "file not found" or "permission denied."
- Database Connection Errors: The database might be offline or a query might fail. Always wrap your database calls in try/catch and check for error messages.
- Incorrect User Input: Users can input unexpected or malicious data. Always validate and sanitize user input
before using it in your logic or passing it to the backend to prevent bugs and security vulnerabilities.
- Invalid JSON or Data Parsing: If your application receives data from an API, a file, or another service, the data might
be in an unexpected format. Always wrap JSON parsing in a try/catch block to prevent a crash.
- switch Statements: Don't forget the default case in your switch statements to handle any unexpected values.
This is crucial for avoiding unhandled logic paths.
- Division by Zero: Just like in C++, dividing by zero will cause an error. Make sure to check that the denominator is not zero before performing any division.
- Promise Rejections: In asynchronous JavaScript, a Promise can "reject" instead of "resolve." Always use .catch() or try/catch with await to handle these rejections gracefully.

- **add more if you find more , its nice to have an errors list to check against**
