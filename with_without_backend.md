

With Backend
- Enables secure user auth, multiplayer state management, persistent storage
- Should ensure cross-browser API and WebSocket support
- You’ll need backend-side error logging and response handling
- Container runs server (PHP or framework), DB, and frontend
Without Backend
- Limits features to local-only or peer-to-peer logic; no centralized user data
- Must handle DOM quirks, caching, or browser inconsistencies entirely in JS
- Client must handle all exceptions gracefully — tricky with peer-to-peer or local-only code
- Container runs only frontend server (e.g. Node/React static server) or just serves static files




# Frontend-Only Architecture
✅ Benefits:
- Simplicity: No need to deploy or maintain a server
- Fast setup: All logic and storage in the browser = fewer moving parts/no db
- Quick sharing: Can be hosted on GitHub Pages, Netlify, or Vercel with minimal fuss
- Great for local demos or prototypes

❌ Drawbacks:
- No secure user accounts (no OAuth, no password verification)
- Data lives only on the user’s device (via localStorage, etc.)
- No multiplayer matchmaking unless using peer-to-peer or third-party services
- Security is minimal — everything is exposed in client-side code
- No centralized leaderboard, chat history, or persistent profiles

# Backend-Enabled Architecture
✅ Benefits:
- Authentication: Can integrate with OAuth2 (e.g., 42 API, Google)
- Real-time multiplayer: Handle matchmaking and game sync via WebSockets
- Persistent data: Store scores, avatars, settings, and chat in a shared database
- Security: Backend can manage JWTs, rate-limiting, 2FA, and data validation
- Modularity: Easier to separate concerns (frontend UI vs. backend logic)

❌ Drawbacks:
- Complexity: Requires knowledge of backend frameworks (NestJS, Express, etc.)
- More setup: Database, server deployment, API routing
- Maintenance overhead: Server uptime, bug tracking, deployment pipelines

# List of mandatory requirements that may require backend:
- 🎮 Player vs. Player Gameplay & Tournament System
    - Real-time multiplayer needs coordination, game state syncing, and persistent player data — difficult (if not impossible) to do securely in the frontend alone. Backend helps manage match queues, results, and tournament flow.
- Protection Against SQL Injections & XSS
    - Implies use of a database, which is a backend component. Securing queries against SQLi is impossible without a server-side layer.
- Must run in Docker	A containerized app
     - typically includes backend services and a database — frontend-only SPA doesn’t justify Docker’s full purpose.
- Authentication & Persistent Profiles (based on module expectations)	OAuth (e.g. 42 API) requires secure token exchange handled server-side. Storing user accounts and scores needs a database and backend logic.
⚠️ Here's What You Lose if you skip a backend:

- User accounts: No persistent login or profiles
- Matchmaking: Hard to support multiplayer unless it's peer-to-peer
- Persistence: No database = scores, history, avatars vanish between sessions
- Security: Client-only apps can't securely manage authentication or sensitive logic

Frontend-only apps = no real persistence

Without a backend, your app can only store data in:
- localStorage (survives reloads, but isn’t secure)
- sessionStorage (gets wiped when the tab closes)
- IndexedDB (a bit more advanced)

But:
These only store data on the user’s own device
You can’t share data across users or keep a central history
You can’t reliably store login sessions or user-specific data (like scores or 2FA)
Cannot do secure authentication due too. 

Frontend-only solutions are fragile, insecure, and local-only
Backend = secure, persistent, centralized data and identity
