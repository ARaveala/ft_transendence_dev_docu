## node.js
Is an open source, cross platform JavaScript runtime environment that lets you run JavaScript code outside the browser,
typically on servers. It’s built on Chrome’s V8 engine, which compiles JavaScript to machine code for fast execution.
It enables full stack development using one language across client and server.

- single threaded unlike cpp which is multi threaded
- automatic garabage collection, c++ developer managed
- supposed to be more beginer friendly than c++


### tools with node.js
- vscode or alternative
- [PM2](https://pm2.io/docs/runtime/guide/process-management/) process manager for productions apps (e.g, Run multiple services like game server + chat server in parallel or local monitoring)
- mocha and chai helps you write and run tests for your backend logic
- webpack module bundler for front end assets (e.g, Serve profile avatars, game sprites, or UI assets)
- nodemon auto restarts server on changes, which lets you test changes instantly

### Plugins and extensibility
Node.js supports a plugin architecture through its module system and NPM ecosystem:

You can build your own plugin system using classes and dynamic imports,
NPM hosts over a million packages, from logging tools to database connectors,
frameworks like Fastify offer plugin based extensibility.

### BEWARE : subject rules state :
"
- The use of libraries or tools that provide an immediate
and complete solution for an entire feature or a module is
prohibited.
- Any direct instruction regarding the use (can, must, can’t) of
a third-party library or tool must be followed.
- The use of a small library or tool that solves a simple, unique
task representing a subcomponent of a larger feature or module,
is allowed.
"

#### common mistakes 

###### Blocking the Event Loop
Node.js is single threaded and relies on a non blocking event loop.
Blocking operations (like synchronous file reads or heavy computations) can freeze the entire app.

Common culprits:

- fs.readFileSync() in request handlers
- CPU-heavy tasks like image processing or encryption

Fix: Use asynchronous alternatives (fs.readFile()) and offload heavy work to worker threads or external services.

###### Misusing require and Module Scope
Improper use of require() can lead to:

- Circular dependencies
- Unintended side effects
- Poor modularization

Fix: Structure code into small, focused modules. Avoid circular imports and use ES Modules (import/export) where possible for better clarity and tooling support.

###### Ignoring Security Best Practices
Node.js apps are often exposed to the web, yet many developers overlook basic security:
- Not validating input (leading to injection attacks)
- Using outdated packages with known vulnerabilities
- Exposing sensitive data in error messages

Fix: Use libraries like helmet and validator,
Keep dependencies updated,
Sanitize all user input

###### Poor Error Handling
Throwing uncaught exceptions or ignoring promise rejections can crash your app or hide bugs.

Common mistakes:

- Forgetting to .catch() promises
- Not using centralized error handling

Fix: Use try/catch with async/await,
Add a global error handler,
Listen for unhandledRejection and uncaughtException events

###### Not Using Environment Variables Properly
Hardcoding secrets (like API keys or DB credentials) into your code is risky and makes deployment inflexible.

Fix: Use .env files and libraries like dotenv to manage configuration:

###### Forgetting to Handle Async Code Correctly
Mixing callbacks, promises, and async/await can lead to messy code and hard-to-track bugs.

Fix: Stick to async/await for consistency,
Avoid callback hell,
Use utility libraries like util.promisify() to convert old-style APIs

###### No Logging or Monitoring
Without logging, you’re flying blind. Many Node.js apps lack visibility into performance, errors, or usage.

Fix: Use winston, pino, or bunyan for structured logging,
Integrate monitoring tools like Prometheus, Grafana, or New Relic

###### Not Cleaning Up Resources
Forgetting to close DB connections, file streams, or timers can lead to memory leaks and degraded performance.

Fix: Use lifecycle hooks or process.on('exit') to clean up,
Always close resources after use
