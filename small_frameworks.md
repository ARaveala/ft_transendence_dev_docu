# What Does “Pure PHP Without Frameworks” Actually Mean?
It means building your backend from scratch in vanilla PHP, without any pre-built frameworks like Laravel, Symfony, Slim, etc.

You would need to handle:
- Manual routing (e.g. parsing $_SERVER['REQUEST_URI'])
- Request parsing and sanitization ($_POST, $_GET)
- Sessions and cookies
- Templating (via raw HTML or PHP includes)
- Database connection (using PDO or mysqli)
- Form validation and security
- Possibly writing your own routing logic and basic controllers
  
⚠️ It’s challenging and time consuming, especially for a game app with login, matchmaking, and real time features.
But thankfully the subject allows us to override this constraint via a framework module.



## quick overview of framework modules **add faremnwork definition somehwere here**
##### IV.2 Web (from subject index)

These modules enable the integration of advanced web features into your Pong game.

- Major module: Use a framework to build the backend.
In this major module, you are required to use a specific web framework for backend
development: Fastify with Node.js .
You can create the backend without using the constraints of this
module by using the default backend language ("If you choose to include a backend, it must be written in pure PHP without
frameworks.").

- Minor module: Use a framework or toolkit to build the front-end.
Your frontend development must use the Tailwind CSS in addition of the Typescript, and nothing else.
You can create a front-end without using the constraints of this
module by using the default front-end directives ("The frontend should be developed using Typescript as base code.")
