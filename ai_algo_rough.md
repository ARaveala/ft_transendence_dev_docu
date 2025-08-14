These modules serve to introduce data-driven elements to the project. The major module
introduces an AI opponent for enhanced gameplay, while the minor module focuses on
user and game statistics dashboards, offering users a minimalistic yet insightful glimpse
into their gaming experiences.

----

## Major module: Introduce an AI opponent.
In this major module, the objective is to incorporate an AI player into the game.
Notably, the use of the A* algorithm is not permitted for this task. Key features
and goals include:
- Develop an AI opponent that provides a challenging and engaging gameplay
experience for users.
- The AI must replicate human behavior, which means that in your AI implementation, you must simulate keyboard input. The constraint here is that
the AI can only refresh its view of the game once per second, requiring it to
anticipate bounces and other actions.
The AI must utilize power-ups if you have chosen to implement the
Game customization options module.
- Implement AI logic and decision-making processes that enable the AI player
to make intelligent and strategic moves.
- Explore alternative algorithms and techniques to create an effective AI player
without relying on A*.
- Ensure that the AI adapts to different gameplay scenarios and user interactions.
You will need to explain in detail how your AI works during your
evaluation. Creating an AI that does nothing is strictly prohibited;
it must have the capability to win occasionally.
This major module aims to enhance the game by introducing an AI opponent that
adds excitement and competitiveness without relying on the A* algorithm.

----

Explanation: This module is about creating an automated player that users can play against, so they don’t always need a human opponent. You'll need to create an algorithm that can make smart decisions without being too difficult to beat.

#### Value of this module:
This module provides a consistent and always-available opponent for players to practice against. This is valuable for new players learning the game or for experienced players who want to test new strategies without waiting for a human opponent. It makes the game more accessible and provides a clear path for skill progression.

###### Beginner-friendly statement:
This is one of the more familiar concepts, as you've likely implemented algorithms in C++. The challenge here is less about the language and more about the strategy. You'll be designing the logic for the AI's "brain" and making sure it can play the game effectively. The learning curve is manageable, as the core idea of an algorithm is something you already know.

#### Modules to be Cautious With:
None. This module is a feature that can be added.

#### Complementary Modules:

- Minor module: Game customization options (AI must use them).
- Major module: Server-Side Pong (AI logic on the server is more secure).

To build this module you will need:
- An algorithm that makes strategic decisions (not A*)
- Backend logic to simulate player input
- Access to the game state to inform the AI's decisions
- A method to limit the AI's "vision" to once per second

---- 

## Minor module: User and Game Stats Dashboards.
In this minor module, the goal is to introduce dashboards that display statistics for
individual users and game sessions. Key features and objectives include:
- Create user-friendly dashboards that provide users with insights into their
gaming statistics.

- Develop a separate dashboard for game sessions, showing detailed statistics,
outcomes, and historical data for each match.
- Ensure that the dashboards offer an intuitive and informative user interface
for tracking and analyzing data.
- Implement data visualization techniques, such as charts and graphs, to present
statistics in a clear and visually appealing manner.
- Allow users to access and explore their own gaming history and performance
metrics conveniently.
- Feel free to add any metrics you deem useful.
This minor module aims to empower users with the ability to monitor their gaming
statistics and game session details through user-friendly dashboards, providing a
comprehensive view of their gaming experience.

---- 

Explanation: This module is about creating a dashboard that shows interesting data about your users and their games, like top scores or recent matches. It's a great way to let users track their progress and see how they stack up against others.

#### Value of this module:
This module provides users with valuable insights into their own performance and the community's activity. This data-driven approach can motivate players to improve, foster a competitive spirit, and allow developers to better understand user behavior and game balance.

###### Beginner-friendly statement:
This module is a great introduction to data visualization. You'll be using a library to take data from your database and turn it into charts and graphs. The learning curve is moderate, as you'll need to learn how to use a new library, but the concepts of filtering and presenting data are likely familiar from your other projects.

#### Modules to be Cautious With:
None. This module is a feature that can be added.

#### Complementary Modules:
- Minor module: Use a database for the backend (SQLite).
- Major module: Standard user management (dashboards are for users' stats).

To build this module you will need:
- A database containing user and game session data
- Backend API endpoints to query stats
- A frontend UI for the dashboards
- A data visualization library (d3.js, Chart.js)
