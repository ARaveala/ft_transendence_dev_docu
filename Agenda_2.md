ft_transcendence Team Meeting Agenda – Backend Coordination

# Quick Recap

## Confirm study group roles:

- Game logic
- Backend (me)
- Database
- Frontend
- Security
- undefined role propose DevOps / Testing / Documentation/security or front end

discoveries or blockers from last week ()
show what we have working as examples or wha texamples will be written

## Integration Planning
- What API routes does the frontend need? (eg, GET /get-user this route states to get user profile maybe, some list of what data the frontend needs to display or interact with and what it will look like when it comes in, what is expected,
eg , wehn recieving user profile , give it without password and return userd id for front end caching?)
- What persistent data does each module expect? (username , any game logic?, tokens)
- Game logic, match results, player stats (some discusion on tournament style )
- Frontend, user settings, avatars? (should avatars be stored in db or locally ? is storing thinsg locally a problem , why?)
- DB schema expectations (email verification if relevant, data structure ie, must contain fields or defaults for missing fields, indexing utalizing localized data for fast look ups and to prevent bottle necking, ie username to id ?)

Define data formats for communication between modules ()

## Security Integration
- How does JWT + 2FA connect to backend?
- What middleware needs to be added to protect routes?
- What does frontend expect after login (token, user object)?
- Does DB need to store session or token metadata?

## Game Logic Interface

- Game is server-side, rendered with Babylon
- Frontend sends input → backend validates → forwards to game logic
- Game logic returns updated state → backend sends to frontend (how will this be managed, will task be split to game and front end)
- Define expected input/output formats 
- Clarify who controls game loop timing

## WebSocket Planning

- WebSocket setup is backend’s responsibility

Define message structure for:
- Player input
- Game state updates
- Match start/end events
- Decide when WebSocket integration begins (before or during coding sprint)

## Testing Strategy

Tools we can use:

- Jest (unit testing)
- Supertest (API route testing)
- Vitest (alternative to Jest, faster for Vite projects)
- Postman (manual API testing)

Assign testing responsibilities

Decide what gets tested first (auth, routing, game logic, all at the same time)

## Docker & Dev Environment

Everyone contributes to Docker setup:?

- Dockerfile for backend 
- Dockerfile for frontend
- docker-compose.yml to link services

School machines don’t allow sudo → avoid volume mounts unless confirmed

Strategy:

- Write and test code without Docker?
then test how it runs inside Docker
- Keep Dockerfiles minimal but functional
- Prepare Makefile for easy build/run commands

## Next Steps

- Route scaffolding details (tell me what you want , nice list with dessired outcome, list prefarbly first simple, then full requirements, id like to give the end points to hit first the refine deeper logic)
- Confirm game logic interface contract
- Begin testing WebSocket structure
- Finalize Dockerfile templates and Compose setup

  ## new
  tournament - tournamnet bracket style

  front end - front pahe user page, tournament page, game page, friends and chat pages?? , login and logout pages, game over winner and looser, error,
  pages are sent how .

  Define the difference between websocket communication of https, so thats its clear for front end 

Decide leftover member’s role (DevOps, QA, Docs)

## testers
- write tester for sql injection nikolai
- game syntax schema

  run inside docker occasionally 


  meeting modnay ....... what time
