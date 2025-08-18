this file should have a somewhat clear idea of what order progression should happen in here is a [link to rough idea](progression_rough.md)

## Meeting agenda
The core of the project sems to be the Docker setup, backend, frontend, and testing,

#### first
- where is everyone at with the previouse projects
- what does everyone already know about the project goals
- what are everyones skill sets
- what modules do people want to do or consider doing

- Who is comfortable with backend languages like Python or Node.js?
- Who is comfortable with frontend technologies like TypeScript and CSS?
- Who is interested in database management and SQL?
- Who has worked with networking, APIs, or WebSockets?
- Who is strong in DevOps, like managing Docker or server deployments?

#### second
Reviewing the Subject Together

- Go through each mandatory module in the project PDF and write down our initial questions.

Specific Questions:
- Web & Hosting: In Inception, we used WordPress. For this project, what is the best way to host our custom-built frontend and backend with Docker? What hosting platform should we consider (e.g., AWS, a local server)?
- Web & Hosting: The PDF mentions hosting with a single container. How do we configure a single docker-compose.yml file to run both the frontend and backend containers together?
- Tool Usage Rules: The PDF says tools that handle an "entire feature" are prohibited. How do we ensure our chosen libraries for the backend and frontend don't violate this rule? What is the line between a "tool" and a "library"?For example, what specific parts of the project will we build from scratch, and what will these tools not solve for us?
- Database: The PDF explicitly says to use SQLite. How do we handle the "Remote Play" and "Tournament" modules with SQLite's single-writer limitation? Do we need to build a separate "leaderboard" table, or will it all be in one place?
- API: Page 25 mentions implementing an API for the Server-Side Pong module. What are the essential endpoints we will need to create? (e.g., POST /api/game/start, GET /api/game/state, POST /api/game/move).


Sectioning Off Study Categories

- How can we divide up the mandatory modules so everyone has a clear learning path?
- Let's make a list of technologies we need to research (e.g., WebSockets for real-time play, SQLite database structure).
- Can we set up a shared document to collect all of our questions and research notes?

#### rough example of workflow as far as i understand it 
- make decisions
- build docker files for front end and back end
      - tools required depend on decisions made
      - there are common tools others have used, a litte time should be spent on seeing if there are better alterantives

Backend Development
- What is the most basic function we can build and test first (e.g., a simple user registration and login using SQLite)?
- Can we build and test the backend without the frontend for now, just to confirm it works?
- What parts can back end devolopement be broken down into 

Frontend Development
- What is the most basic frontend component we can build to test the backend (e.g., a login form)?
- How can we build and test the frontend's look and feel without a live backend connection?
- What parts can front end developement be broken down into
  
Communication and Collaboration
- How will we share code and collaborate effectively?
- What is our strategy for committing and pushing code to our repository?
- How often will we have quick check-in meetings?

Here are some apparently easy to use tools that will help you maintain code quality and test your work as you go.

- Prettier
What it's for: Code formatting. Prettier automatically reformats your code to a consistent style, so you don't have to worry about spacing, line breaks, or indentation.

Why it's useful: It ensures all code you write looks the same across the team, which is great for readability and collaboration.

- ESLint
What it's for: Finding errors and enforcing coding style. ESLint analyzes your code to catch common mistakes and stylistic issues based on a set of rules you can configure.

Why it's useful: It helps you catch bugs early and maintains a high level of code quality. It's like a spell checker for your code.

- Thunder Client
What it's for: API testing. Thunder Client is a lightweight alternative to Postman that lives directly in VS Code. It lets you send requests to your backend endpoints and see the responses.

Why it's useful: You can test your backend API immediately after building it without needing to write any frontend code. This is perfect for verifying that your Docker setup and backend logic are working correctly.

- Jest
What it's for: Unit and integration testing. Jest is a JavaScript testing framework that makes it easy to write and run tests for your code. It's commonly used with Node.js and TypeScript.

Why it's useful: It allows you to write automated tests that check if small parts of your code (units) or entire features (integrations) are working as expected, which is essential for a complex project like this.
