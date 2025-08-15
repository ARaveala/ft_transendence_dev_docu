this file needs checking at the moment its fully ai with strict prompt. fixing requires drawing to previouse experiences and checking validity of any suggestions
🗃️ SQLite Overview
SQLite is a lightweight, serverless SQL database that stores all data in a single file. It’s widely used in mobile apps, embedded systems, and small-scale web applications due to its simplicity and portability.

⚙️ Key Characteristics
- Single-file storage: All data is stored in one .sqlite file, making it easy to move or back up.
- No server required: SQLite runs in-process with your application—no need to install or manage a separate database server.
-Easy setup: Just include the SQLite library and start querying. Ideal for quick prototyping or local development.

| Feature | SQLite | MariaDB |
| ----- | ----- | ----- |
| **Architecture** | Serverless, embedded | Client-server model |
| **Storage** | Single file | Multi-file, managed by server |
| **Concurrency** | Limited (single writer) | High concurrency with row-level locking |
| **SQL Features** | Basic subset | Full SQL support (joins, procedures, etc.) |
| **User Management** | None (manual implementation required) | Built-in users, roles, and permissions |
| **Performance** | Great for small apps | Scales well for large, multi-user systems |
| **Use Case** | Mobile apps, local tools, small web apps | Web servers, enterprise apps, cloud DBs |


🌐 Multi-user and Remote Access Considerations
- SQLite is not designed for high-concurrency or remote access scenarios. This is a critical point for your project.
- Single Writer Limitation: SQLite uses database-level locking, meaning only one write operation can occur at a time. Multiple simultaneous writes can cause contention, slowdowns, or failures.
- Remote Access Challenges: SQLite is file-based and doesn't support remote connections natively. You'd need to expose it via an API, which is the correct approach for your project.

The Key to Remote Play
This is where your central game server comes in. For remote play, players don't talk to the SQLite file. They connect to your server, which acts as the game's central hub. The server has two main jobs:

Handling Live Gameplay: It runs the game logic in real-time, processing things like player movements and scoring updates. All the players send their actions to this server, and the server sends back what everyone needs to see on their screens. This communication happens very quickly using an API. This live data is stored in the server's temporary memory for speed.

Managing the Database: Only the server talks to the SQLite database file. It's the one that decides when to save or load persistent data.

To prevent data loss if a player disconnects, your server can periodically save checkpoints to the SQLite database during a match. This adds a layer of safety without compromising the speed of real-time play.

Why Not Multiple SQLite Files?
It's tempting to think that multiple files could solve problems, but it actually creates more. Using a single database file for your entire project is standard practice and aligns with the project's design:

Simplicity and Consistency: Managing one file is much simpler than managing a file for every player or every tournament. All your data is in one consistent location.

Data Integrity: A single file prevents the problem of data getting out of sync. For example, if a player's name changes, you only need to update it in one place.

Architectural Guidance: The project is guiding you toward a common and professional system design where all data is handled by a central server through a single database.

🔐 Access Control and User Management
SQLite does not support built-in user roles or authentication. You must implement access control at the application level:

Use app-level logic to restrict access to certain queries or data.

Protect the .sqlite file with OS-level permissions.

⚖️ Benefits and Limitations
✅ Benefits

Lightweight and fast for small apps

Zero configuration—no server setup

Portable—just copy the file

Reliable for embedded and mobile use cases

ACID-compliant with transactional support

❌ Limitations

Poor concurrency—single writer at a time

Limited SQL features—no stored procedures, full outer joins, etc.

Loose typing—can lead to unexpected behavior

No built-in user management

Not ideal for remote or distributed systems

🚫 Common Beginner Mistakes
Treating it like a server-based DB: SQLite is not designed for high-concurrency or remote access. Trying to scale it like PostgreSQL or MariaDB leads to frustration.

Skipping backups: Since everything is in one file, corruption or accidental deletion can be catastrophic without backups.

Module Constraints
Based on the project PDF, here are the key constraints you must follow:

Database Module: You must use SQLite as the designated database for all instances.

Server-Side Pong Module: You must have a central server that runs the game logic. This module is the key to enabling remote play without relying on the database for real-time data.

Third-Party Libraries: The use of unapproved libraries is at the discretion of the evaluator. Using something like PostgreSQL would likely be seen as a violation of the mandatory SQLite requirement.
SQLite uses database level locking, meaning only one write operation can happen at a time. If multiple parts of your app try to write simultaneously, things can slow down or even fail.
Everything is stored in one file. That’s great for portability, but it can become a bottleneck for large scale apps or when you need distributed access.
performance tends to degrade once you hit a few gb especially without careful indexing and query optimization
No stored procedures, limited trigger support, and no full outer joins. If your app or framework expects these features, you’ll need workarounds
SQLite doesn’t offer robust user management or access control like PostgreSQL or MySQL. If your app needs fine-grained permissions, you’ll have to implement them manually
SQLite uses “manifest typing,” which means it doesn’t strictly enforce column types. This can lead to unexpected behavior if your app assumes strict typing
Easy to set up no server required
Often used in mobile apps and browser extensions
check how compatible SQLlite is against modules

---
ai dump because im going down a rabit hole 
What is SQLite?
Think of SQLite as a tiny, self-contained database that lives in a single file on your computer. Unlike larger databases like PostgreSQL, it doesn't need a separate server running to work. It's a serverless database that is perfect for a single program or a single person to use at one time.

Because it's just a file, you can't have multiple players from different computers all trying to change it at the same time over the internet.

The Key to Remote Play
This is where your central game server comes in. For remote play, players don't talk to the SQLite file. They connect to your server, which acts as the game's central hub.

The server has two main jobs:

Handling Live Gameplay: It runs the game logic in real-time, processing things like player movements and scoring updates. All the players send their actions to this server, and the server sends back what everyone needs to see on their screens. This communication happens very quickly using an API.

Managing the Database: Only the server talks to the SQLite database file. It's the one that decides when to save or load information.

Handling Different Types of Game Data
To make this work, you need to think about two kinds of data:

Live Data: This is the temporary, fast-changing information during a game, like a player's current score or the position of the ball. This data is kept in the server's temporary memory so it can be accessed almost instantly without slowing the game down.

Persistent Data: This is the long-term information you want to save. Once a game or tournament is finished, the server takes the final results from its temporary memory and saves it to the SQLite database. This includes player names, final scores, and tournament details.

This way, the game stays fast and responsive, and your data is safely stored in the database for later use.
