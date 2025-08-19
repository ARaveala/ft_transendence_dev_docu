## what do you mena backend


1.What will back end handle consider modules:
Back end module (1)
Front end module (0.5)
database module (0.5)
user management (1)
Game customization options. (0.5)
game graphics with babylon (1)
Major module: Introduce an AI opponent. (1) easy to add later
Multiple language support (0.5)
Minor module: Expanding Browser Compatibility (0.5)
Implement Two-Factor Authentication (2FA) and JWT (1)

2. what does the docker file need for backend to start with

- start with a base image : Specify the base operating system and language runtime. For example, using Node.js, we start with a Node image: FROM node:18-alpine. (node:18 , debian has fuller packages
- and maybe be easier when working with sql lite)
- Copy Files: Copy your backend source code into the container.
- Install Dependencies: Run the commands to install your project's dependencies (e.g.,node.js, npm install).
      - node.js
      - npm (package installer)
      - fastify ?
- Set the Working Directory: Define the main directory where your application will live inside the container.
- Expose a Port: Tell Docker which port your server will be listening on. This is crucial for other containers or your host machine to connect to it.
- Run the Server: Define the command that starts your server when the container launches. For example, CMD ["npm", "start"].
- front end and backend have their own dockerfiles, yaml will run and connect them together.
- docker-compose.yml file can use an Nginx container to serve the frontend files.

3. Backend (my Role):
- primary role managing persistent data.
- Responsible for the API, but it would handle things like:
    - User registration and login.
    - Storing user profiles.
    - Saving game outcomes (who won, the final score).
    - Managing a leaderboard.

The WebSocket communication would be much simpler, perhaps just for a chat feature or for a spectator mode, but not for synchronizing the live game.

Backend Container: This is a self-contained box that holds nothing but your backend server and its dependencies.
Its only job is to run your API and handle things like database operations and real-time communication. It doesn't know or care about how the frontend looks.

In the context of this project, "backend" means the server-side component that handles all the logic and data.

Here's a breakdown of what that means specifically for your project:

What the Backend Does:
- Server Hosting: The backend is the code that runs the web server. This server will be listening for requests on a specific address and port (e.g., localhost:4343).
- API Endpoints: It exposes the API (Application Programming Interface). When the frontend (which is just a bunch of HTML/CSS/JS files in the browser) needs to do something,
- like log a user in or get their profile data, it sends a request to a specific URL on your backend server.
The backend receives this request, processes it, and sends back a response.

- Real-Time Communication: The backend manages the WebSockets for real-time play. When a player moves their paddle, their frontend sends a message to the backend via the WebSocket.
The backend then immediately broadcasts that new paddle position to all other connected players.

- Database Management: The backend is the only thing that interacts with the SQLite database file.
It handles all the reading and writing of persistent data, like player scores, user profiles, and tournament details.

The Workflow from Your Perspective:

- You build the backend code: You'll write the code that sets up the server, defines the API endpoints, and manages the database connection.

- You create a Dockerfile: This file tells Docker how to package your backend code and its dependencies (like the SQLite library) into a self-contained container.

- You run the container: When you execute docker-compose up, Docker starts your backend container. This container then starts your web server.

- You access it from the frontend: Your frontend container (which is separate) will serve the static HTML/CSS/JS files to your browser. That frontend code will be configured to make its API calls to the backend container's address (e.g., http://backend-service:8080).

### so far what i understand about what needs to be done in backedn in general
- create database and connect to it (sqlite3, jyst ebcause its more common?)
- create end points (GET/user:id, POST/add-user, DELETE/user:id) (must ask front end what is needed for them, if there are any naming conventions to follow)
- 
### input parsing
what errors should be displayed for logs only and what for users, eg incorrect username format for users, will we use schemas for all of this
- score values (number, positive or negative)
        - number
        - positive or negative values (ask front end, how do we want scoring to work, will we be sent pre calculated value or are we doing the math backend)
        - underflow overflow unexisting values
        - minimum maximum score
        - if win/loose , reset?
        - tournament scores will have different rules what?
  - usernames
          - duplicate name handling
          - potentially harmful characters in name (if the characters are likley to confuse code)


## what i might need to know extra
- what ORM is being used for database
- anyother tools anyone is using i should list, they may affect what i need to do and how to do it
