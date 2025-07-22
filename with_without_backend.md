
# 🧠 Backend vs Frontend-Only: Architecture Overview

This document outlines what each approach enables, limits, and demands — based on ft_transcendence constraints.

---

## ⚙️ With a Backend

### ✅ Pros
- **User Authentication**: OAuth2 login (e.g. 42 API or Google)
- **Multiplayer Support**: Real-time game coordination via WebSockets
- **Persistent Data**: Scores, profiles, settings, chat logs in a shared database
- **Security**: Backend can sanitize inputs, handle JWTs, and protect against SQL injection/XSS
- **Matchmaking & Tournament Management**: Queue players, schedule matches, and display who’s playing
- **Aliases Across Sessions**: Track player names, reset automatically with each tournament
- **Docker Friendly**: Runs full backend server and DB in one container
- **Error Handling**: Central place to log and respond to unexpected behavior

### ❌ Cons
- Requires backend setup: server, database, API routes
- Higher complexity (e.g. PHP or framework module)
- More files and services to maintain
- Deployment involves more configuration

---

## 🧁 Without a Backend (Frontend-Only)

### ✅ Pros
- Easy to develop and deploy
- All logic runs in the browser (no server needed)
- Can host on GitHub Pages, Netlify, or Vercel
- Suitable for local demos and prototypes
- Docker image can be minimal (static site or lightweight frontend server)

### ❌ Cons
- **No persistent login or user accounts**
  - Can’t verify identity or use OAuth2
- **No centralized data**
  - Scores, aliases, and game history live only in browser
- **Multiplayer limited**
  - Peer-to-peer possible (via WebRTC), but unstable and hard to scale
- **Matchmaking impossible**
  - Can’t schedule players across devices or sessions
- **No server-side validation**
  - Vulnerable to cheating, spoofing, and XSS/SQLi risks
- **No shared chat history**
  - Can only use localStorage or in-memory — wiped on refresh
- **Reset logic must be manual**
  - Tournament info and aliases must be cleared per session/device

---

## 🔍 Mandatory Project Requirements & Backend Implications

| Requirement | With Backend | Without Backend |
|------------|--------------|-----------------|
| Local multiplayer (same keyboard) | ✅ Not required | ✅ Fully supported |
| Remote multiplayer (via module) | ✅ Required | ⚠️ Limited via WebRTC, no persistence |
| Tournament system | ✅ Full support with DB | ⚠️ Only local simulation, no shared state |
| Registration system (aliases) | ✅ Aliases stored in DB | ⚠️ Limited to localStorage or memory |
| Matchmaking & next match display | ✅ Server-side queue | ❌ Not possible across devices |
| Paddle speed & AI fairness | ✅ Can enforce server-side | ✅ Can be enforced via frontend logic |
| Security (SQLi/XSS) | ✅ Can sanitize server inputs | ❌ Cannot prevent malicious manipulation |
| Docker deployment | ✅ Full-stack container | ✅ Simple static site container |
| SPA with Back/Forward nav | ✅ Yes | ✅ Yes (via frontend routing) |
| TypeScript frontend | ✅ Required (unless overridden) | ✅ Required (unless overridden) |

---

## 🧠 TL;DR Summary

- A **frontend-only** setup can meet minimum criteria for a demo with local multiplayer and interface.
- A **backend** is strongly recommended if you want authentication, remote matchmaking, tournament control, persistent scores, and security.
- Certain project expectations (like protection against SQLi/XSS or organizing matches across players) imply server-side infrastructure — even if the document technically allows frontend-only development.

---
