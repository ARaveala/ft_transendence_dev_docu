These cybersecurity modules are designed to enhance the security posture of the project.
The major module focuses on robust protection through Web Application Firewall (WAF)
and ModSecurity configurations, as well as HashiCorp Vault for secure secrets management. The minor modules complement this effort by adding features for GDPR compliance, user data anonymization, account deletion, Two-Factor authentication (2FA),
and JSON Web Tokens (JWT), collectively ensuring the project’s commitment to data
protection, privacy, and authentication security.

----

## Major module: Implement WAF/ModSecurity with Hardened Configuration and
HashiCorp Vault for Secrets Management.
The objective of this major module is to enhance the security infrastructure of the
project by implementing several key components. Key features and goals include:
◦ Configure and deploy a Web Application Firewall (WAF) and ModSecurity
with a strict and secure configuration to protect against web-based attacks.
◦ Integrate HashiCorp Vault to securely manage and store sensitive information,
such as API keys, credentials, and environment variables, ensuring that these
secrets are properly encrypted and isolated.
This major module aims to bolster the project’s security infrastructure by implementing robust security measures, including WAF/ModSecurity for web application
protection and HashiCorp Vault for secrets management to ensure a safe and secure
environment.

----
Explanation: This module is about using advanced tools to protect your website from hackers and securely store important passwords and keys. The Web Application Firewall (WAF) acts as a shield against common attacks, while the Vault is like a digital safe for your secrets.

#### Value of this module:
This module significantly enhances the application's security posture. The WAF protects against common web attacks, and HashiCorp Vault provides a secure, centralized way to manage sensitive secrets like API keys and database credentials, which is a critical best practice for production environments.

###### Beginner-friendly statement:
This module is heavy on new concepts, as it deals with advanced infrastructure and security tools. The learning curve is very steep, and you'll be dealing with tools that don't have direct parallels in C++. The challenge is in understanding how these components work together to protect your application, rather than low-level coding. This is a module for those who want a deep dive into professional-grade security practices.

#### Modules to be Cautious With:
None. This module overrides the simple .env secret management method, which is a good practice.

#### Complementary Modules:
- Major module: Designing the Backend as Microservices (WAF and Vault are well-suited for securing distributed systems).

To build this module you will need:
- A reverse proxy server (NGINX, Caddy)
- The ModSecurity module configured with a hardened rule set
- A HashiCorp Vault container
- Backend logic for services to authenticate with and retrieve secrets from Vault

----

## Minor module: GDPR compliance options with user anonymization, local data
management, and account deletion.
The goal of this minor module is to introduce GDPR compliance options that allow
users to exercise their data privacy rights. Key features and objectives include:
◦ Implement GDPR-compliant features that enable users to request anonymization of their personal data, ensuring that their identity and sensitive information are protected.
◦ Provide tools for users to manage their local data, including the ability to
view, edit, or delete their personal information stored within the system.
◦ Offer a streamlined process for users to request the permanent deletion of
their accounts, including all associated data, ensuring compliance with data
protection regulations.
◦ Maintain clear and transparent communication with users regarding their data
privacy rights, with easily accessible options to exercise these rights.
This minor module aims to enhance user privacy and data protection by offering
GDPR compliance options that empower users to control their personal information
and exercise their data privacy rights within the system.
If you are not familiar with the General Data Protection Regulation (GDPR), it
is essential to understand its principles and implications, especially regarding user
data management and privacy. The GDPR is a regulation that aims to protect the
personal data and privacy of individuals within the European Union (EU) and the
European Economic Area (EEA). It sets out strict rules and guidelines for organizations on how they should handle and process personal data.
To gain a better understanding of the GDPR and its requirements, it is strongly
recommended to visit the official website of the European Commission on data
protection1
. This website provides comprehensive information about the GDPR,
including its principles, objectives, and user rights. It also offers additional resources to delve deeper into the topic and ensure compliance with the regulation.
If you are unfamiliar with the GDPR, please take the time to visit the provided link
and familiarize yourself with the regulations before proceeding with this project.

----

Explanation: This module is about making sure your application follows rules for how to handle user data, especially for users in Europe. It involves building features that allow users to manage their data, like deleting their account or requesting a copy of their information.

#### Value of this module:
This module ensures your application is legally compliant with a major data privacy regulation. This builds user trust by demonstrating a commitment to protecting their personal data and gives them control over their information, which is a key component of modern digital citizenship.

###### Beginner-friendly statement:
This module is a great way to learn about the legal and ethical side of software development. It's less about coding and more about understanding the requirements of data privacy. The learning curve is moderate, as you'll need to learn how to implement features like account deletion, but the core concepts are straightforward.

#### Modules to be Cautious With:
Major module: Store the score of a tournament in the Blockchain. As mentioned before, blockchain's immutability conflicts with the GDPR's "right to be forgotten" and data deletion rules. You can't truly "forget" data on a public ledger.

#### Complementary Modules:
- Minor module: Use a database for the backend (SQLite).
- Major module: Standard user management.

To build this module you will need:
- Database management logic for data anonymization and deletion
- A user interface for data management requests
- A process for account deletion

----
## Major module: Implement Two-Factor Authentication (2FA) and JWT.
The goal of this major module is to enhance security and user authentication
by introducing Two-Factor Authentication (2FA) and utilizing JSON Web Tokens
(JWT). Key features and objectives include:
◦ Implement Two-Factor Authentication (2FA) as an additional layer of security
for user accounts, requiring users to provide a secondary verification method,
such as a one-time code, in addition to their password.
◦ Utilize JSON Web Tokens (JWT) as a secure method for authentication and
authorization, ensuring that user sessions and access to resources are managed
securely.
◦ Provide a user-friendly setup process for enabling 2FA, with options for SMS
codes, authenticator apps, or email-based verification.
◦ Ensure that JWT tokens are issued and validated securely to prevent unauthorized access to user accounts and sensitive data.
This major module aims to strengthen user account security by offering Two-Factor
Authentication (2FA) and enhancing authentication and authorization through the
use of JSON Web Tokens (JWT).

----

Explanation: This module adds an extra layer of security to user logins. After entering their password, users must also provide a unique code from their phone, making it much harder for someone else to access their account. JSON Web Tokens (JWTs) are then used to securely manage the user's session without a database.

#### Value of this module:
This module provides a robust layer of security beyond a simple password. 2FA is a critical security feature for protecting user accounts from unauthorized access. The use of JWTs offers a stateless and scalable way to manage user sessions, which is ideal for modern, distributed applications.

###### Beginner-friendly statement:
This module introduces two new and important security concepts. The idea of 2FA is a new protocol, but it's a logical flow to implement. JWTs are a completely new way of thinking about sessions. Unlike a traditional C++ program where a user might be authenticated for a single session, JWTs allow you to create a secure, verifiable "token" that proves a user's identity without requiring a database lookup every time. The learning curve is steep, but the concepts are critical for modern web development.

#### Modules to be Cautious With:
None. This module is a security enhancement.

#### Complementary Modules:
- Major module: Standard user management (builds on a standard login system).
- Major module: Live Chat (JWTs secure WebSocket connections).

To build this module you will need:
- A backend library for JWTs (jsonwebtoken, jose)
- A library for generating and validating 2FA codes (speakeasy, otpauth)
- Database storage for user 2FA secrets
- Frontend UI for the 2FA setup and verification process

