## Major module: Replace Basic Pong with Server-Side Pong and Implementing an
API.
In this major module, the goal is to replace the basic Pong game with a serverside Pong game, accompanied by the implementation of an API. Key features and
objectives include:
◦ Develop server-side logic for the Pong game to handle gameplay, ball movement, scoring, and player interactions.
◦ Create an API that exposes the necessary resources and endpoints to interact
with the Pong game, allowing partial usage of the game via the Command-Line
Interface (CLI) and web interface.
◦ Design and implement the API endpoints to support game initialization, player
controls, and game state updates.
◦ Ensure that the server-side Pong game is responsive, providing an engaging
and enjoyable gaming experience.
◦ Integrate the server-side Pong game with the web application, allowing users
to play the game directly on the website.
This major module aims to elevate the Pong game by migrating it to the server
side, enabling interaction through both a web interface and CLI while offering an
API for easy access to game resources and features.

----
Explanation: This module is a crucial change that moves the game's logic from the user's browser to the server. This makes the game more secure and reliable, as it prevents players from cheating and ensures all players are synchronized in real time.

#### Value of this module:
This is a critical step for building a fair and cheat-proof multiplayer game. By centralizing the game logic on the server, you ensure that all players are seeing the same, truthful game state, which is essential for competitive integrity and a better user experience.

###### Beginner-friendly statement:
This is a huge step in complexity from a simple, client-side C++ game. The learning curve is steep because you are no longer just running a game loop on one machine. You will be introduced to WebSockets for real-time communication, a new paradigm for state management, and the challenge of making the server the single source of truth for the game.

#### Modules to be Cautious With:
This module overrides the mandatory part's default client-side Pong implementation.

#### Complementary Modules:
- Major module: Remote players.
- Major module: Enabling Pong Gameplay via CLI against Web Users.
- Major module: Live Chat.

To build this module you will need:
- A backend game loop
- A RESTful API for game session management
- A library for real-time communication (WebSockets, Socket.IO)
- Game physics and collision detection logic on the server
- Security measures to prevent cheating

----

## Major module: Enabling Pong Gameplay via CLI against Web Users with API
Integration.
In this major module, the goal is to develop a Command-Line Interface (CLI) that
allows users to play Pong against players using the web version of the game. The
CLI should connect to the web application seamlessly, enabling CLI users to join
and interact with web players. Key features and objectives include:
◦ Create a robust CLI application that replicates the Pong gameplay experience
available on the website, providing CLI users with the ability to initiate and
participate in Pong matches.
◦ Utilize the API to establish communication between the CLI and the web
application, enabling CLI users to connect to the site and interact with web
players.
◦ Develop a user authentication mechanism within the CLI, allowing CLI users
to log in to the web application securely.
◦ Implement real-time synchronization between the CLI and web users, ensuring
that gameplay interactions are seamless and consistent.
◦ Enable CLI users to join and create Pong matches with web players, facilitating
cross-platform gameplay.

◦ Provide comprehensive documentation and guidance on how to use the CLI
effectively for Pong matches against web users.
This major module aims to enhance the Pong gaming experience by creating a CLI
that seamlessly connects CLI users to web players through API integration, offering

----

Explanation: This module is about creating a separate way to play the game using a command-line interface (CLI). This allows a user to play from a terminal against players who are using the web version of the game.

#### Value of this module:
This module creates a unique and powerful way to interact with the game. It demonstrates a strong understanding of different client types and how to build a unified system that supports diverse user interfaces, from a simple command line to a rich web app.

###### Beginner-friendly statement:
This module is a great way to apply your C/C++ knowledge of command-line tools to a web project. The learning curve is moderate, as you'll be writing a new client that communicates with your server. The concepts are familiar, but you'll need to learn how to make network requests and handle real-time data in a command-line environment.

#### Modules to be Cautious With:
None. This module is a feature that can be added.

#### Complementary Modules:
- Major module: Replace Basic Pong with Server-Side Pong... (this module is a prerequisite).
- Major module: Remote players.

To build this module you will need:
- A command-line application (e.g., built with Python or Node.js)
- An HTTP client to make API calls to the server (axios, node-fetch)
- A WebSocket client to receive real-time game state (ws, socket.io-client)
- A text-based UI to display the game in the terminal
- A method for handling user input from the command line
a unified and interactive gameplay environment.
If you wish to complete this module, we strongly recommend that you
do the previous one.
