this page is yet to be constructed , here should be links to different tools.
links should be some explanation with 1 or more websource and or youtube video , id you add a youtube video please make sure you have seen it first and it has some educational value . 
if the information can be labeled well even better 
link to where we came from if possible here 

## fastify 
if this tool is used to fullfill a module , typescript will not be available.
Fastify is a high performance web framework for building backend applications in Node.js.

#### tools with fastify
- vscode or alternative, vscode provides a selection of uself extensions that can help colaboration run smoother.
- node.js , runtime environment , like running compiled c++ but for js
- npm or pnpm package manager , like apt but for js, pnpm is appartently more superior , it uses symlinks.
- postman or curl api testing, same as using curl in bash to test endpoints (send packet and inspect reply).
- ESLint code linter, like cppcheck or clang-tidy (these can be extensions on vscode they help show code correctness as based on a certain standard)
- Prettier code formatter like clang-format for constinet styling, usefull if multiple people are colaborating in shared scope.
- fastify CLI prohject scaffolding , like using cmkae or make

Fastify handles all the server-side logic. That includes:

- Managing player data (scores, profiles, matchmaking) (alternative options form other modules?) 
- Routing / Handling HTTP requests (like when a player joins a game or sends a move)
- Connecting to databases to store and retrieve game info
- Serving APIs to your frontend (so the Pong interface can talk to the server)
- Schema Validation Automatically check incoming data (like JSON) for correctness, this helps prevent thinsg like block injection attacks.
    - In C++, we would manually check if a char* is null or if a number is within bounds. In python we might use assert or try/except. Fastify does this automatically using a schema.
- Logging like with	printf, spdlog	Fastify uses Pino
- Error handling
- Lifecycle hooks

It’s built on Node.js, so you’ll be writing backend code in JavaScript
```npm install -g fastify-cli
fastify generate my-app```
This sets up a project with:
- Predefined folder structure
- app.js as the entry point
- routes/ and plugins/ folders
- Ready to run server with npm run dev
- .json replaces makefile 
It’s like using cmake or make to scaffold a C++ project

### 🔌 Popular Fastify Plugins You Might Use
@fastify/cors: Handles cross-origin requests (important if your frontend is hosted separately)

@fastify/env: Manages environment variables securely

@fastify/swagger: Generates interactive API docs

@fastify/jwt: Adds JSON Web Token authentication

@fastify/static: Serves static files like images or frontend assets

These plugins are modular, so you only include what you need — keeping your backend lean and fast1.

Here’s what Fastify offers to make backend development smoother:

Feature	What It Does
- 🔄 Routing	Defines how your server responds to different URLs (e.g. /start-game, /get-score)
- 📦 Plugin System	Lets you add features like logging, authentication, or CORS without cluttering your core code
- 📑 Schema Validation	Ensures incoming data (like player names or scores) is valid using JSON Schema
- 🔐 Security Plugins	Easily add protections like rate limiting, input sanitization, and HTTPS support
- 📊 Logging	Built-in support for fast, structured logging using Pino
- ⚡ Performance	One of the fastest Node.js frameworks thanks to its low overhead and efficient routing
- 🔄 Async/Await Support	Clean, modern syntax for handling asynchronous operations like database queries
🧩 Swagger Integration	Auto-generates API documentation with plugins like @fastify/swagger

#### random notes 
✅ Many student repositories use Fastify with Node.js successfully, often alongside tools like Prisma (ORM), Redis (caching), and Vite (frontend bundler).
⚠️ Deployment Expectations: Deployment isn’t officially required by the school, but many students go the extra mile to deploy using Docker, Nginx, and HTTPS. This can introduce complexity if you're not careful with Fastify’s static file serving or socket configuration.
## node.js
is a programming language 
runs in browser comparible to python
