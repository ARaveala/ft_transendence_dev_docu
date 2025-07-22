API - a set of rules and protocols that allows different software applications to communicate with each other

---
#### OAuth2

OAuth2 is an authorization protocol that lets users log in using external services (e.g. Google, GitHub, school intranet), without sharing their password directly with your site. Instead, it exchanges secure tokens to verify identity between systems.

### 🔐 Why Use OAuth2?
- Offloads credential management to trusted providers
- Simplifies account creation and login
- Useful if you're connecting to platforms like the 42 API or any centralized user database

### ⚠️ Restrictions in This Project

You **cannot use libraries or tools** that:
- Provide a **complete out-of-the-box OAuth solution** (e.g. `passport`, `Auth0`, `NextAuth`)
- Implement the entire login flow on your behalf

✅ You **can** use:
- Small utilities that handle **subtasks** (e.g. parsing a redirect URL or encoding a token)
- Manual integration: sending your own requests to an OAuth provider, handling redirects, and managing tokens manually

🧠 Note: OAuth2 is **not required** for ft_transcendence. You can implement a local alias system or custom login instead.

<details>
<summary><em>Example (Manual OAuth2 Flow)</em></summary>

Let’s say your team chooses to use the 42 API for user login. Here’s how you could approach it **without violating constraints**:

1. **Redirect user to 42’s login URL** with proper client ID and scopes  
   → You can hardcode or generate this manually

2. **User logs in**, and 42 redirects back to your site with an authorization code  
   → You capture this code in your frontend or backend

3. **Exchange the code for a token** using a POST request from your server  
   → Manual `curl` or native PHP logic — no external library needed

4. **Store the token** securely (server-side or in a cookie)  
   → Use it to authenticate the user across the session

This way, you’re respecting the rule: **you’re not importing a full OAuth module**, you’re stitching the flow together piece by piece.

</details>

---


## Token based authentication

A method where users are identified using a temporary, secure token (usually a string or session ID) issued after login. The server validates this token with each action to confirm the user’s identity, without needing to store passwords or credentials long-term.

- Can be used with simple alias systems or full login flows
- Does **not require OAuth2**
- Useful for verifying players during tournaments, chat messages, or game submissions

<details>
<summary><strong>Example</strong></summary>

> Think of how you created a session in **webserv**: after a user logged in, you might have stored a session ID in a cookie or header. Each subsequent request checked that ID to confirm the user was valid — *that's token-based authentication.*
>
> Similarly, in **ft_irc**, each client had to introduce itself (e.g. with a nickname) before sending commands. While it wasn't technically a "token," the concept is similar: assign an identity, and validate it before letting the user interact.
>
</details>
This approach lets you build custom lightweight security for things like tournament actions, chat messages, and match submissions, even if you're not using full login systems or external identity providers.

---

## Websockets

WebSockets are a protocol that creates a **persistent, two-way connection** between a user's browser and your server. Unlike traditional HTTP (which sends a request and then closes), WebSockets stay open, making them ideal for live interaction.

### 🔧 What They’re Used For
- **Real-time Pong gameplay** (syncing ball and paddle positions)
- **In-game chat** (players see each other's messages instantly)
- **Live match updates** (e.g. "Next match: Alice vs Bob")
- **Player status events** (disconnects, score changes)

### 🔄 How They Keep Data Live
Once a WebSocket connection is opened, both client and server can push data to each other **at any time**, without needing to refresh the page or send separate HTTP requests.

<details>
<summary><strong>Example1</strong></summary> 
   
> Bob moves his paddle → browser sends a WebSocket message to server  
> Server immediately forwards that to Alice’s browser  
> Alice sees Bob’s paddle move, in real time

This keeps gameplay smooth, without delay or polling.
</details>



### 🛡️ Security & Sanitation
WebSockets are just a data channel, they don’t sanitize anything by default.

You **must** manually clean and validate anything users send:
- **On the server**, before storing or rebroadcasting (SQLi risk)
- **On the client**, before displaying in the DOM (XSS risk)

<details>
<summary><strong>Example2</strong></summary>
 
> A user sends a chat message with weird code or unexpected HTML  
> If you display it without filtering, it could break your page — or worse, run scripts  
> Always treat WebSocket messages like *untrusted input*

### 🧪 Beginner-Friendly Example
WebSockets commonly transmit data using lightweight JSON messages , here is a clean and maliciouse message:

```json
{
  "event": "chat",
  "sender": "Alice",
  "message": "Good luck!"
}

{
  "event": "chat",
  "sender": "Alice",
  "message": "<img src='x' onerror='alert(\"Hacked!\")'>"
}
```
</details>

---
