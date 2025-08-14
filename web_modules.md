# Major module: Use a framework to build the backend.
----
In this major module, you are required to use a specific web <a href="Definitions.md#frameworks " title="software framework that is designed to support the development of web applications ">framework</a> for backend
development:  [fastify](fastify.md)  with [node.js](node_js.md).

You can create the backend without using the constraints of this
module by using the default backend language [php without frameworks](small_frameworks.md). However, this module will only be valid if you
follow its requirements. This means using only fastify with node.js . 

----

Explanation: A framework gives a pre-built structure and tools to create the server side logic of your website, saving us from writing everything from scratch. It helps you organize your code for things like handling user requests and connecting to a database.

#### Value of this module:
Using a web framework provides a structured and efficient way to build the backend of your application. Compared to writing raw server logic or using PHP without frameworks, this module offers:

- request handling and plugin support, allowing for more rapid development and testing.
- security tools that help mitigate vulnerabilities like XSS attacks.
-access to node.js ecosystem tools like ESLint and testing frameworks that improve collaboration and code quality.
- flexibility with easier integration with databases and real-time communications.

###### Beginner-friendly statement:
Transitioning from C++ to a web backend framework can feel like a big leap. While the core logic of a server might be familiar (like a main function), a framework introduces concepts like automated request handling and asynchronous programming. It's a steep curve, but it provides a clear structure, so you don't have to build the whole server from scratch. Think of it as learning to use a powerful std:: library for the web, where a lot of the low-level work is handled for you.

#### Modules to be Cautious With: 
The mandatory requirement for "pure PHP without frameworks." This module directly overrides that constraint, so it's a choice you make instead of the default.

#### Complementary Modules:
- Minor module: Use a database for the backend (SQLite)
- Major module: Store the score of a tournament in the Blockchain
- Major module: Designing the Backend as Microservices

To build this module you will need:
- A Node.js runtime and package manager (npm, yarn)
- A backend web framework (Fastify, Express (its available in fastify, must confirm module validity of using it ))
- A project structure for backend code (routes, controllers)
- A method for handling environment variables (dotenv)
- Integration with other module's APIs (axios, node-fetch)

 ----
# Minor module: Use a framework or toolkit to build the front-end.
Your frontend development must use the [Tailwind CSS] in addition of the [Typescript](typescript.md), and nothing else.

Note: If graphics module is chosen the use of babylon may overwrite this module if babylon is not used carefully.

You can create a front-end without using the constraints of this
module by using the default front-end directives (The frontend should be developed using Typescript as base code). However, this module will only be valid if you follow its requirements.

----

Explanation: A frontend framework helps you build a dynamic and interactive user interface without having to manually update every part of the page with raw JavaScript. It provides reusable components and makes it easier to manage how your website looks and feels.

Note: choosing default with typescript as base opens up options to use :

- React (with or without Next.js)
- Vue.js (with or without Nuxt)
- Angular
- Svelte or SvelteKit
- SolidJS
- amongs a very large list of other alternatives .

Many of these options may increase learning curve and lack of advice and help from other students .

#### Value of this module:
This module significantly improves the developer experience by providing a structured, component-based approach to building the user interface. It facilitates creating complex, interactive UIs, offers a declarative way to manage the frontend state, and makes the code easier to maintain and scale.
- You don’t need to master full CSS syntax tailwind provides ready to use classes, and typescript helps structure your logic, this makes styling more intuitive and keeps your HTML and CSS tightly connected, reducing the need to jump between files (reduces context switching),you write markup, styling, and logic all in one place (usually .tsx files). .
- responsive design such as screen sizes are easier managed through tailwind
  

###### Beginner-friendly statement:
Coming from C++, the idea of a frontend framework like React can be a completely new way of thinking. Instead of writing sequential code, we will be building the UI with "components" — reusable pieces that handle their own logic and display. This requires learning new languages like JavaScript and concepts like asynchronous operations. However, the framework's structure is consistent, and once you understand the core principles, it makes building complex UIs much more manageable.

#### Modules to be Cautious With:
The mandatory part's default frontend constraints. This module is an explicit choice to use a framework.

#### Complementary Modules:
- All modules with a visual component, as Tailwind will provide the styling foundation.
- Minor module: Support on all devices (Tailwind is responsive by design).

To build this module you will need:
- A frontend library/framework (React, Vue)
- TypeScript for core frontend logic
- A CSS framework (Tailwind CSS)
- A build tool like Vite or Webpack
- An HTML entry point for the single-page application

----
# Minor module: Use a database for the backend -and more.
The designated database for all DB instances in your project is [SQLite](sqllite.md) This choice
ensure data consistency and compatibility across all project components and may
be a prerequisite for other modules, such as the backend Framework module.

---- 

Explanation: A database is like a digital filing cabinet for all your website's important information. Choosing this module means you will have a place to save data like user profiles, game results, and settings, so it doesn't disappear when you close the application.

#### Value of this module:
This module enables data persistence, which is essential for any dynamic application. It allows you to save and retrieve user profiles, game statistics, and other critical information, which is a foundational requirement for features like user accounts, leaderboards, and personalized experiences.
- Simple no config and serverless
- Runs locally so 0 network latency
- Ideal for ready heavy operations (not ideal for write heavy)
- Data base is stored in a file , this aids crossplatform and running on multiple machines without complex setup.
- Since the entire database is a single file, backups are as simple as copying it. Great for versioning, rollback and testing.
- Each player can have their own SQLite file, and each tournament can also be stored in a separate file. This modular structure simplifies data access, reduces write conflicts, and improves data safety by isolating operations per user or event.

###### Beginner-friendly statement:
Using a database might be one of the most familiar concepts here if you've done file I/O in C or C++. A database is simply a more structured and powerful way to store data on disk. While we will need to learn a new query language (SQL), the fundamental idea of reading and writing information is similar to what we already know. The learning curve is manageable, and it's a core skill for almost any web application.

----
# Major module: Store the score of a tournament in the Blockchain.
This Major module focuses on implementing a feature within the Pong website to
securely store tournament scores on a [blockchain]. It is essential to clarify that for
development and testing purposes, we will use a [testing blockchain] environment.
The chosen blockchain for this implementation is [Avalanche] , and [Solidity] will be
the programming language used for smart contract development.

◦ Blockchain Integration: The primary goal of this module is to seamlessly integrate blockchain technology, specifically Avalache , into the Pong website.
This integration ensures the secure and immutable storage of tournament
scores, providing players with a transparent and tamper-proof record of their
gaming achievements.
◦ Solidity Smart Contracts: To interact with the blockchain, we will develop
Solidity smart contracts. These contracts will be responsible for recording,
managing, and retrieving tournament scores.
◦ Testing Blockchain: As mentioned earlier, a testing blockchain will be used for
development and testing purposes. This ensures that all blockchain-related
functionalities are thoroughly validated without any risks associated with a
live blockchain.

◦ Interoperability: This module may have dependencies on other modules, particularly the Backend Framework module. Integrating blockchain functionality
might require adjustments in the backend to accommodate interactions with
the blockchain.

By implementing this module, we aim to enhance the Pong website by introducing
a blockchain-based score storage system. Users will benefit from the added layer
of security and transparency, ensuring the integrity of their gaming scores. The
module emphasizes the use of a testing blockchain environment to minimize risks
associated with blockchain development.

----

Explanation: This module is about using blockchain technology to create a public, tamper-proof record of game scores. Once a score is added to the blockchain, it cannot be changed or deleted, which can be useful for transparent and fair tournaments.

#### Value of this module:
This module ensures a public, transparent, and unchangeable record of tournament scores. By leveraging blockchain technology, you eliminate the possibility of cheating or tampering with results, providing a high level of trust and integrity to the tournament system.
- cool factor, being able to show off blockchain understanding (decentralized tech.)

######  Beginner-friendly statement:
This is one of the most conceptually challenging modules, as it involves a completely new paradigm of distributed ledgers. The learning curve is very steep. You'll need to learn a new language like Solidity and understand concepts like smart contracts, gas fees, and decentralized networks, which have no direct parallel in C/C++. This is a bonus challenge for someone looking to dive deep into a cutting-edge field.

#### Modules to be Cautious With:
- Minor module: GDPR compliance options. This is a classic conflict. The core tenet of blockchain is immutability, which directly clashes with the GDPR's "right to be forgotten" and the ability to delete user data.

#### Complementary Modules:
- Major module: Use a framework to build the backend (for API communication with the blockchain).
- Minor module: User and Game Stats Dashboards (to pull and display blockchain scores).

To build this module you will need:
- Solidity for smart contract development
- A local Avalanche testnet environment or a public testnet
- A smart contract development framework (Hardhat, Truffle)
- A library for your backend to interact with the blockchain (Web3.js, ethers.js)
- A user interface to display on-chain scores

if we want to consider the option later, code must be kept modular, all score logic as seperate as possible. 


