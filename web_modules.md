# Major module: Use a framework to build the backend.
In this major module, you are required to use a specific web framework for backend
development:  [fastify](fastify.md)  with [node.js](node_js.md).

You can create the backend without using the constraints of this
module by using the default backend language [php without frameworks](small_frameworks.md). However, this module will only be valid if you
follow its requirements. This means using only fastify with node.js .If graphics module is chosen the use of babylon will overwrite this module. 

```
<a href="Definitions.md#token-based-authentication " title="A method where users are identified using a temporary, secure token (like a string or ID) issued after login.">
```
link to definition web framework to be included

#### value of this module 

Using a web framework  provides a structured and efficient way to build the backend of your application. Compared to writing raw server logic or using PHP without frameworks, this module offers:

- request handling and plugin support , allows for more rapid developement and testing.
- security tools that help mitigate vunralbilities like XSS attacks
- access to to node.js ecosystem tools leik ESLint and testing frameworks improves collaboration and code quality
- flexability with easier integration with databse and real time communications ([websockets])

 
# Minor module: Use a framework or toolkit to build the front-end.
Your frontend development must use the Tailwind CSS in addition of the Typescript, and nothing else.

You can create a front-end without using the constraints of this
module by using the default front-end directives (The frontend should be developed using Typescript as base code). However, this module will only be valid if you follow its requirements.

internal link to typescript to be added.


# Minor module: Use a database for the backend -and more.
The designated database for all DB instances in your project is [SQLite](sqllite.md) This choice
ensure data consistency and compatibility across all project components and may
be a prerequisite for other modules, such as the backend Framework module.


below yet to have links to tools applied
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
