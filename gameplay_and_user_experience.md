:note this file needs a bit more depth

These modules are designed to enhance the overall gameplay experience of the project.

----
## Major module: Remote players
It should be possible for two players to play remotely. Each player is located on a
separated computer, accessing the same website and playing the same Pong game.

Consider network issues, such as unexpected disconnections or lag.
You must offer the best user experience possible.

----

Explanation: This module moves the game from a single-computer, two-player experience to a multiplayer game where players can compete against each other from different computers. It requires a backend to handle communication between the players in real-time.

#### Value of this module:
This module transforms a single machine game into a true multiplayer experience. It expands the game's audience and replayability by allowing users to play against anyone, anywhere. It also introduces new technical challenges like
real time synchronization and network management, which are core to modern game development.

###### Beginner-friendly statement:
This is a fundamental shift from a simple C++ game where everything runs on one machine. The learning curve is steep because you are no longer thinking about just your game loop; you're thinking about real-time communication via WebSockets, network latency, 
and synchronizing a single game state across multiple machines.
It's a big, but worthwile, challenge in understanding how networked applications work.

#### Modules to be Cautious With: 
The mandatory part's "same keyboard" requirement. This module is an explicit choice to move beyond that.

#### Complementary Modules:
- Major module: Live Chat (for inviting players).
- Major module: Server-Side Pong (for synchronizing game state).
- Major module: Multiple players (extends the concept to more than 2 players).

To build this module you will need:
- A real time communication protocol (WebSockets, Socket.IO)
- A backend to manage game sessions
- Frontend logic to send player inputs
- A strategy to handle network latency and disconnections

----

## Major module: Multiple players
It should be possible to have more than two players. Each player needs live control
(so the “remote players” module is strongly recommended). It’s up to you to decide
how the game could be played with 3, 4, 5, 6 or more players.

Along with the regular 2 players game, you can define a specific number of players,
greater than 2, for this multiplayer module. Ex: 4 players could play on a square board,
with each player controlling one unique side of the square.

----

Explanation: This module expands the game beyond a one on one match, allowing for more
than two players to join a single game. It will require a new game design and a backend
that can manage the state of a more complex match.

#### Value of this module:
This module greatly enhances the social and competitive aspect of the game by allowing
more than two players to compete at once. This opens up opportunities for new game modes
and cooperative experiences, which can increase user engagement and retention.

###### Beginner-friendly statement:
Building on the remote players module, this one adds complexity to the game state itself.
The core concepts from C++ like arrays and data structures will be useful here,
but we will be applying them in a networked context.
The learning curve is steep because you have to account for more than two inputs and outputs,
but it's a logical extension of the real time communication we will have already implemented.

#### Modules to be Cautious With:
The mandatory part's "same keyboard" requirement. This module is an explicit choice to move beyond that.

#### Complementary Modules:
- Major module: Remote players (as a prerequisite).
- Major module: Server-Side Pong (for managing a multi-player game state).

To build this module you will need:
- A backend game engine that can handle multiple players (provide details)
- A new game board layout (e.g., a square board)
- WebSockets to synchronize all players' actions
- A matchmaking system for grouping multiple players

----

## Major module: Add another game with user history and matchmaking.
The goal of this major module, is to introduce a new game, distinct from Pong, and
incorporate features such as user history tracking and matchmaking. Key features
and objectives include:
◦ Develop a new, engaging game to diversify the platform’s offerings and entertain users.
◦ Implement user history tracking to record and display individual users’ gameplay statistics.
◦ Create a matchmaking system to allow users to find opponents and participate
in fair and balanced matches.
◦ Ensure that user game history and matchmaking data are stored securely and
remain up-to-date.
◦ Optimize the performance and responsiveness of the new game to provide an
enjoyable user experience. Regularly update and maintain the game to fix
bugs, add new features, and enhance gameplay.
This major module aims to expand your platform by introducing a new game,
enhancing user engagement with gameplay history, and facilitating matchmaking
for an enjoyable gaming experience.

----

Explanation: This module is about creating a second, entirely different game within your application. It also requires you to store
game results in a database and build a system that can pair players up for a match.

#### Value of this module:
This module diversifies the application by offering more than one type of game, which can significantly increase user retention and provide a more comprehensive platform. The matchmaking system and
user history also add a competitive layer, encouraging players to return and improve their skills.

###### Beginner-friendly statement:
This module is a great way to put all your new skills together.
It's not about learning a new core technology, but about applying what we have learned
about databases, user management, and game logic to build a new feature from start to finish.
The challenge lies in organizing the code and making the new game integrate smoothly with
the existing system.

#### Modules to be Cautious With: None.
This module is a core feature that can be added without conflicting with others.

#### Complementary Modules:
- Minor module: Use a database for the backend (SQLite).
- Major module: Remote players (the new game can also be remote).
- Minor module: Game customization options.

To build this module you will need:
- The complete game logic on the frontend
- A matchmaking algorithm on the backend
- A database to store user gameplay history
- Backend API endpoints for the new game
- A user interface to display game history and initiate matches

----

## Minor module: Game customization options.
In this minor module, the goal is to provide customization options for all available
games on the platform. Key features and objectives include:

◦ Offer customization features, such as power-ups, attacks, or different maps,
that enhance the gameplay experience.
◦ Allow users to choose a default version of the game with basic features if they
prefer a simpler experience.
◦ Ensure that customization options are available and applicable to all games
offered on the platform.
◦ Implement user-friendly settings menus or interfaces for adjusting game parameters.
◦ Maintain consistency in customization features across all games to provide a
unified user experience.

This module aims to give users the flexibility to tailor their gaming experience
across all available games by providing a variety of customization options while
also offering a default version for those who prefer a straightforward gameplay
experience.

----

Explanation: This module is about giving users the ability to change game settings to theirliking.
This could include things like power ups, different maps, or other visual changes that enhance
the gameplay experience.

#### Value of this module:
This module empowers users to personalize their gameplay experience,
which can lead to increased engagement and a stronger sense of ownership over the game.
It allows for creative freedom and can be a key differentiator from other simple game implementations.

###### Beginner-friendly statement:
This module is not very difficult from a technical perspective.
It's about designing a user interface for settings and learning how to save those settings,
likely in a database. The learning curve is low, and the concepts are similar to what we might do
with a configuration file in C++.

#### Modules to be Cautious With:
None. This module is an additive feature unless used beyond game graphics, then the backend module
might be overwritten if used for clickable buttons on website.

#### Complementary Modules:
- Major module: Introduce an AI opponent (the AI must be able to use the customizations).
- Major module: Add another game... (customizations would apply to the new game as well).

To build this module you will need:
- A settings menu on the frontend
- Database storage for user specific preferences
- Game logic to implement customizations (e.g., power-ups, different maps)

----

## Major module: Live Chat.
In this module, you need to create a chat feature for users:
◦ The user should be able to send direct messages to other users.
◦ The user should be able to block other users, preventing them from seeing any
further messages from the blocked account.
◦ The user should be able to invite other users to play a Pong game through the
chat interface.
◦ The tournament system should be able to notify users about the next game.
◦ The user should be able to access other players’ profiles through the chat
interface.

----

Explanation: This module adds a real time chat feature to our application, allowing users
to communicate with each other instantly. It’s great for inviting friends to play or
just for general conversation between players.

#### Value of this module:
This module facilitates real time communication between players, turning the application into
a social hub. This allows for direct interaction, such as inviting friends to games
or discussing strategies, which significantly improves the user experience.

###### Beginner-friendly statement:
This module is another great opportunity to learn about real time communication.
we will be using WebSockets, which is a new concept for bidirectional communication.
While the core idea of sending and receiving messages is simple, understanding how to
manage multiple users and a history of messages adds a layer of complexity.

#### Modules to be Cautious With:
None. This module enhances user interaction.

#### Complementary Modules:
- Major module: Standard user management (chat needs user identities).
- Major module: Remote players (for inviting players).
- 
To build this module you will need:
- A backend chat server using WebSockets
- A database to store chat history and block lists
- Frontend UI for the chat window
- Backend logic for direct messages and notifications




