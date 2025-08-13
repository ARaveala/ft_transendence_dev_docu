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

The User Management module is central to the project and works best when paired with: links to modules to be provided
- Secure authentication
- Social features
- GDPR tools
- Tournament tracking

But it requires careful handling when integrating:
- Blockchain (due to immutability)
- Microservices (due to tight coupling)

To build this module, you’ll need:
- Authentication tools (OAuth, JWT, 2FA)
- User management logic (Fastify routes, SQLite schema or potentially other databse)
- Security practices (password hashing, input validation) (eg bcrypt)
- Tournament linkage (relational DB design)
- User routes like login and registartion is handled by backend (eg, fastify)
- Secure credential storage , no leaks can be handled using eg , zod, joi what else project safe methods 


## Major module: Implement remote authentication.
In this major module, the goal is to implement the following authentication system:
Google Sign-in .

Key features and objectives include:
- Integrate the authentication system, allowing users to securely sign in.
- Obtain the necessary credentials and permissions from the authority to enable
secure login.
- Implement user-friendly login and authorization flows that adhere to best practices and security standards.
- Ensure the secure exchange of authentication tokens and user information
between the web application and the authentication provider.
This major module aims to provide a remote user authentication, offering users a
secure and convenient way to access the web application.
