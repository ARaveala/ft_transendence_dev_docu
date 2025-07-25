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

----
- Major module: Use a framework to build the backend.
In this major module, you are required to use a specific web framework for backend
development: Fastify with Node.js .
You can create the backend without using the constraints of this
module by using the default backend language ("If you choose to include a backend, it must be written in pure PHP without
frameworks.").

<details>
  <summary><strong>❌ Issues You Might Face:</strong></summary>

- Conflict with Default Backend Language Enabling this module overrides the requirement to use pure PHP.  So you cannot use PHP at all in your backend if this module is active.
- Incompatible with Modules Expecting PHP-based Functionality Modules that assume native PHP functions (e.g. mailers, file handlers, or legacy scripts) may not work.
- You Must Follow Fastify’s Structure Routes, handlers, WebSocket support — everything must conform to Fastify’s conventions.
- Added Setup Complexity You’ll need Node.js tooling, TypeScript config (if used), and probably module bundling.
- Docker Adjustments Fastify needs different ports, environment setup, and build layers than a PHP-based backend especially tricky in rootless Docker.
- Conflict with Default Backend Language Enabling this module overrides the requirement to use pure PHP. → So you cannot use PHP at all in your backend if this module is active.
- Incompatible with Modules Expecting PHP-based Functionality Modules that assume native PHP functions (e.g. mailers, file handlers, or legacy scripts) may not work.
- You Must Follow Fastify’s Structure Routes, handlers, WebSocket support — everything must conform to Fastify’s conventions.
- Added Setup Complexity You’ll need Node.js tooling, TypeScript config (if used), and probably module bundling.
- Docker Adjustments Fastify needs different ports, environment setup, and build layers than a PHP-based backend — especially tricky in rootless Docker.
❌ Cannot reuse PHP’s session_start(), $_COOKIE, etc.

❌ Cannot reuse any PHP code — the language is gone

Instead, you’ll use Fastify-compatible systems:

✅ fastify-jwt or fastify-cookie for tokens/sessions

✅ Middleware for authentication checks

✅ JSON-based validation with fastify-schema
</details>

---
- Minor module: Use a framework or toolkit to build the front-end.
Your frontend development must use the Tailwind CSS in addition of the Typescript, and nothing else.
You can create a front-end without using the constraints of this
module by using the default front-end directives ("The frontend should be developed using Typescript as base code.")

<details>
  <summary><strong>❌ Issues You Might Face:</strong></summary>

- Frontend Is Now Restricted to Tailwind + TS Only You cannot use other CSS libraries (e.g. Bootstrap, Bulma) or raw CSS styles. → All styling must be done using Tailwind classes.
- No JS Frameworks Allowed React, Vue, Svelte? ✖️ Not permitted in this module unless explicitly allowed elsewhere.
- Component Logic Must Stay within TypeScript You’ll need to handle game UI, DOM updates, and animations using raw TypeScript instead of high-level abstractions.
- Bundling Required Likely need a build tool (e.g. Vite or Webpack) to process Tailwind and TypeScript correctly.

</details>
