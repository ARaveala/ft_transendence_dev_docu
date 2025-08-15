## III.4 Security concerns

The project requires basic security practices. You must protect against common web vulnerabilities like Cross-Site Scripting (XSS),
SQL Injection, and Cross-Site Request Forgery (CSRF). You also need to securely store passwords, so you can't save them as plain text.

In order to create a functional website, there are several security concerns you must
address:
- Any password stored in your database, if applicable, must be hashed.
<a href="Definitions.md#password-hashing" title="a cryptographic process that converts a plaintext password into a fixed-length string of characters.">small definition of hashed passwords</a>
- Your website must be protected against <a href="Definitions.md#sql-injection" title="a web security vulnerability that allows an attacker to interfere with the queries a web application makes to its database.">SQL injections</a>/
<a href="Definitions.md#xss-cross-site-scripting" title="a type of security vulnerability found in web applications that allows attackers to inject malicious client-side scripts into web pages viewed by other users.">XSS attacks</a>.
- If you have a backend or any other features, it is mandatory to enable an HTTPS[what does this mean ]
connection for all aspects (use wss instead of ws for example).
- You must implement validation mechanisms for forms and any user input, either on
the base page if no backend is used, or on the server side if a backend is employed.
- Regardless of whether you choose to implement the JWT Security module with
2FA[link to details 2FA], it’s essential to prioritize the security of your website. For instance, if you
choose to create an API[waht do you mean if we choose API?], ensure your routes are protected. Even if you decide not
to use JWT tokens, securing the site remains critical.
[why might we not use JWT]

Please make sure you use a strong password hashing algorithm

For obvious security reasons, any credentials, API keys, env
variables etc., must be saved locally in a .env file and ignored
by git. Publicly stored credentials will cause your project to fail.

Modules that help fulfill the requirements
- Major module: Implement Two-Factor Authentication (2FA) and JWT: This module is a direct way to enhance the security of user logins.
- Major module: Implement WAF/ModSecurity... and HashiCorp Vault...: This module is an advanced solution for protecting against many of the vulnerabilities mentioned, such as XSS and SQL Injection.
- Minor module: Use a database for the backend: A secure database and proper data sanitization are essential for preventing SQL Injection attacks.
