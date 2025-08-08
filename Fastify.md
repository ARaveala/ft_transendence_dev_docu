links should be some explanation with 1 or more websource and or youtube video , if you add a youtube video please make sure you have seen it first and it has some educational value that you understand. 

## fastify 
if this tool is used to fullfill a module , typescript will not be available even though it is compatible due to module completion requirements.
Fastify is a high performance web framework for building backend applications in Node.js.

#### tools with fastify
- vscode or alternative, vscode provides a selection of uself extensions that can help colaboration run smoother.
- node.js , runtime environment , like running compiled c++ but for js outside the browser
- npm or pnpm package manager , like apt but for js, pnpm is appartently more superior , it uses symlinks.
- postman or curl api testing, same as using curl in bash to test endpoints (send packet and inspect reply).
- ESLint code linter, like cppcheck or clang-tidy (these can be extensions on vscode they help show code correctness as based on a certain standard)
- Prettier code formatter like clang-format for constinet styling, usefull if multiple people are colaborating in shared scope.
- fastify CLI project scaffolding , like using cmkae or make

Fastify handles all the server-side logic. That includes:

- Managing player data (scores, profiles, matchmaking) (alternative options form other modules?) 
- Routing (uses a radix tree)/ Handling HTTP requests (like when a player joins a game or sends a move)
- Connecting to databases to store and retrieve game info
- Serving APIs to your frontend (so the Pong interface can talk to the server)
- Logging fastify uses Pino (comparative too printf, spdlog)
- Schema Validation Automatically check incoming data (like JSON) for correctness, this helps prevent things like block injection attacks.
- Error handling, can be more automatic then with c++.
- Lifecycle hooks, event driven callbacks, triggered by the framework at key stages. (You don’t need to remember to call the function it’s automatic once set up.)

[link to a few fastify examples](fastify_examples.md) 
(please feel free to add more examples, make sure to keep things simple and provide links for information expansion, this prevents being immadatley overwhelmed)

It’s built on Node.js, so you’ll be writing backend code in JavaScript

### scaffold fastify with
```
npm install -g fastify-cli
fastify generate my-app
```

This sets up a project with:
- Predefined folder structure
- app.js as the entry point
- routes/ and plugins/ folders
- Ready to run server with npm run dev
- package.json (similar role to makefile)

It’s like using cmake or make to scaffold a C++ project

### 🔌 Popular Fastify Plugins You Might Use
Applying a plugin is done using the .register() method. some plugins may accept options like setting file paths or configuration of things like security.
- @fastify/cors: Handles cross-origin requests (important if your frontend is hosted separately)
- @fastify/env: Manages environment variables securely
- @fastify/swagger: Auto generates interactive API docs...(a bit confused still)
- @fastify/jwt: Adds JSON Web Token authentication
- @fastify/static: Serves static files like images or frontend assets (e.g serving profile avatars or HTML)
- @fastify/redis: caching, sessions storage (eg, for matchmaking or live game updates)
- @fastify/websocket: Adds websocket support for real time communication , essential for live pong gameplay.
- @fastify/formbody: Parses application/x-www-form-urlencoded form data (useful for login forms)
- @fastify/helmet : Adds security headers to protect against common web vulnerabilities (eg, protection against XSS attacks)
- @fastify/rate-limit: Prevents abuse by limiting how often users can hit your API
- @fastify/multipar: Handles file uploads (e.g. profile avatars)

These plugins are modular, so you only include what you need.

[getting started official fastify.dev](https://fastify.dev/docs/latest/Guides/Getting-Started/)

[fastify examples and templates](https://codesandbox.io/examples/package/fastify)

[fastify playground on git](https://github.com/ktm-m/playground-fastify) : this uses MySQL, our data base choice will be limited to SQLlite. 


#### common mistakes 

###### Plugin management:
Creating deeply nested plugin structures, often referred to as "plugin hell," which can make code difficult to read, understand, and maintain.
This complexity can lead too:
- the need for global variables to manage state or dependencies across different plugin contexts.
- confusing encaspulation issues
- plugins failing silently due to suppressed errors 

If a plugin needs to expose something (like a DB connection) to the parent scope, it must be wrapped with fastify-plugin otherwise, its decorators stay encapsulated.
Failing to do so can result in inaccessible resources, (such as a database connection), which are encapsulated within the plugin's own context.

Suppressing plugin errors using after() is discouraged, as it can hide critical failures (e.g broken DB connections or duplicate routes).

fix: use pluggins to modularize cleanly, and wrap shared resources with ``` fastify-plugin ```when needed.

###### schema validation
Many begginers skip this, this can lead to unexpected bugs and security issues.
Apparently most errors in Fastify stem from invalid or unexpected input so , proper input validation is essential for robust error handling and error prevention in general.

fix: Define schemas for each route to ensure clean, predictable data.

###### ignoring lifecycle hooks
Fastify offers hooks like onRequest, preHandler, etc., but they’re underused,
missing out on centralized logging, auth checks, or performance monitoring.

Fix: Use hooks for global logic:

###### Serving static files incorrectly
Beginners often try to serve static files manually or forget to use @fastify/static, this can lead to 
broken image links or inaccessible frontend assets.

Fix: Use the plugin properly to serve files like avatars, CSS, or JS:

###### not enabling loggin
Fastify has built in logging via pino, but for some reason it’s often disabled during development, this leads to 
harder debugging, no visibility into requests or errors and missed preformance insights.

Fix: Enable logging from the start


#### random notes 
Many student repositories use Fastify with Node.js successfully, often alongside tools like Prisma (ORM), Redis (caching), and Vite (frontend bundler).
(tool validity must be checked).

Deployment Expectations: Deployment isn’t officially required by the school, but many students go the extra mile to deploy using Docker, Nginx, and HTTPS. This can introduce complexity if you're not careful with Fastify’s static file serving or socket configuration.


