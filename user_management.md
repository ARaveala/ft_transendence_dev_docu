This module delves into the realm of User Management, addressing key aspects of
user interactions and access control within the Pong platform. It encompasses two major
components, each focused on essential elements of user management and authentication: user participation across multiple tournaments and the implementation of remote
authentication.


## Major module: Standard user management, authentication and users across tournaments.
- Users can securely subscribe to the website.
- Registered users can securely log in.
- Users can select a unique display name to participate in tournaments.
- Users can update their information.
- Users can upload an avatar, with a default option if none is provided.
- Users can add others as friends and view their online status.
- User profiles display stats, such as wins and losses.
- Each user has a Match History including 1v1 games, dates, and relevant
details, accessible to logged-in users.

The management of duplicate usernames/emails is at your discretion;
please ensure a logical solution is provided.

Explanation: This module is about creating a system that allows users to create accounts, log in with a username and password, and manage their profiles. It’s the essential starting point for any features that are specific to a logged-in user.

#### Modules to be Cautious With: 
None. This module provides a foundational service for other modules, making them easier to implement.

#### Complementary Modules:
- Minor module: Use a database for the backend (SQLite)
- Major module: Implement Two-Factor Authentication (2FA) and JWT
- Major module: Remote authentication (as an alternative login method)
- Major module: Live Chat

To build this module you will need:
- A database to store user data, including hashed passwords
- User-facing forms for registration and login
- A secure password hashing library (bcrypt.js, argon2)
- Session management or a token-based authentication system
- File storage for user avatars

Essential for: Fulfilling the mandatory user authentication requirement and providing the foundation for any user-specific features like profiles, chat, and game history.

## Major module: Implement remote authentication.
In this major module, the goal is to implement the following authentication system:
Google Sign-in .

Key features and objectives include:
- Integrate the authentication system, allowing users to securely sign in.
- Obtain the necessary credentials and permissions from the authority to enable
secure login.
- Implement user-friendly login and authorization flows that adhere to best practices and security standards. [provide link to defintion of user friendly and best practises and security standards]
- Ensure the secure exchange of authentication tokens and user information
between the web application and the authentication provider.

Explanation: This module gives users the option to log in using an external service, such as Google. Instead of creating a new username and password, they can use their existing account from another service. This provides a convenient and trusted way for users to access the application.

#### Modules to be Cautious With:
None. This is an alternative login method that can coexist with standard user management.

#### Complementary Modules:
- Major module: Standard user management (as an alternative login method).
- Major module: Implement Two-Factor Authentication (2FA) and JWT (JWTs are used for session management after the initial Google sign-in).

To build this module you will need:
- A backend to handle the OAuth2 flow
- Google Cloud Console credentials
- A client-side library to initiate the sign-in process (react-google-login)
- A backend library to verify the authentication token (google-auth-library)
- A database to store user information retrieved from Google

This major module aims to provide a remote user authentication, offering users a
secure and convenient way to access the web application.
