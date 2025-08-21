ft_transcendence Team Meeting Agenda – Backend Coordination

📌 Quick Recap

Confirm study group roles:

Game logic

Backend (me)

Database

Frontend

Security

Leftover role → propose DevOps / Testing / Documentation

Share any discoveries or blockers from last week

🔗 Integration Planning

What API routes does the frontend need?

What persistent data does each module expect?

Game logic → match results, player stats

Frontend → user settings, avatars?

DB → schema expectations

Define data formats for communication between modules

🛡️ Security Integration

How does JWT + 2FA connect to backend?

What middleware needs to be added to protect routes?

What does frontend expect after login (token, user object)?

Does DB need to store session or token metadata?

🎮 Game Logic Interface

Game is server-side, rendered with Babylon

Frontend sends input → backend validates → forwards to game logic

Game logic returns updated state → backend sends to frontend

Define expected input/output formats

Clarify who controls game loop timing

🌐 WebSocket Planning

WebSocket setup is backend’s responsibility

Define message structure for:

Player input

Game state updates

Match start/end events

Decide when WebSocket integration begins (before or during coding sprint)

🧪 Testing Strategy

Tools we can use:

Jest (unit testing)

Supertest (API route testing)

Vitest (alternative to Jest, faster for Vite projects)

Postman (manual API testing)

Assign testing responsibilities

Decide what gets tested first (auth, routing, game logic)

🐳 Docker & Dev Environment

Everyone contributes to Docker setup:

Dockerfile for backend

Dockerfile for frontend

docker-compose.yml to link services

School machines don’t allow sudo → avoid volume mounts unless confirmed

Strategy:

Write and test code without Docker

Then test how it runs inside Docker

Keep Dockerfiles minimal but functional

Prepare Makefile for easy build/run commands

🛠️ Next Steps

Assign route scaffolding tasks

Confirm game logic interface contract

Begin testing WebSocket structure

Finalize Dockerfile templates and Compose setup

Decide leftover member’s role (DevOps, QA, Docs)
