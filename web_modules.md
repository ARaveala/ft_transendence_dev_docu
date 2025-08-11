# Major module: Use a framework to build the backend.
In this major module, you are required to use a specific web <a href="Definitions.md#frameworks " title="software framework that is designed to support the development of web applications ">framework</a> for backend
development:  [fastify](fastify.md)  with [node.js](node_js.md).

You can create the backend without using the constraints of this
module by using the default backend language [php without frameworks](small_frameworks.md). However, this module will only be valid if you
follow its requirements. This means using only fastify with node.js . 

#### value of this module 

Using a web framework  provides a structured and efficient way to build the backend of your application. Compared to writing raw server logic or using PHP without frameworks, this module offers:

- request handling and plugin support , allows for more rapid developement and testing.
- security tools that help mitigate vunralbilities like XSS attacks
- access to to node.js ecosystem tools leik ESLint and testing frameworks improves collaboration and code quality
- flexability with easier integration with databse and real time communications (<a href="Definitions.md#websockets " title="  a communication protocol that provides a persistent, bidirectional, full-duplex channel over a single TCP connection">[websockets]</a>)

 
# Minor module: Use a framework or toolkit to build the front-end.
Your frontend development must use the [Tailwind CSS] in addition of the [Typescript](typescript.md), and nothing else.

Note: If graphics module is chosen the use of babylon may overwrite this module if babylon is not used carefully.

Optionally we can opt to use babylon and utalize tools allowing us to write a different module faster.Rendering UI Inside Babylon Instead of HTML
If we use Babylon to create buttons, menus, or overlays inside the 3D canvas (e.g., using Babylon GUI), we will be bypassing Tailwind CSS and HTML.
** this must be double checked that it dosnt disqualify us completley **


You can create a front-end without using the constraints of this
module by using the default front-end directives (The frontend should be developed using Typescript as base code). However, this module will only be valid if you follow its requirements.

Note: choosing default with typescript as base opens up options to use :

- React (with or without Next.js)
- Vue.js (with or without Nuxt)
- Angular
- Svelte or SvelteKit
- SolidJS
- amongs a very large list of other alternatives .

Many of these options may increase learning curve and lack of advice and help from other students .

#### value of this module
- Tailwind’s utility first (class based) approach keeps styling clean and predictable. You apply design directly in your markup using reusable class names, the logic shares similarities with cpp because of this which will help the learning curve.
- more variety in online resources (when probelm solving)
- You don’t need to master full CSS syntax tailwind provides ready to use classes, and typescript helps structure your logic, this makes styling more intuitive and keeps your HTML and CSS tightly connected, reducing the need to jump between files (reduces context switching),you write markup, styling, and logic all in one place (usually .tsx files). .
- Type safety meaning code is checked for errors before it runs, typeScript ensures that variables, props, and functions behave as expected. Tailwind doesn’t directly affect type safety, but when paired with TypeScript, you get smart suggestions for props, event handlers, and even HTML attributes. Autocomplete works better because TypeScript understands your code structure, and Tailwind plugins can suggest valid class names as you type.
- responsive design such as screen sizes are easier managed through tailwind
- editor tools and extensions for vscode share similarities with backend by choices made and are more readily ailable with this combo 
With markup, styling, and logic all in one .tsx file, you avoid context switching between HTML, CSS, and JS

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


### potential contradictions with other modules.
- gdpr module [provide link here ] GDPR Article 17 gives users the “right to be forgotten”, blockchain data is immutable once written, it cannot be deleted. (may be able to beat the system depending of choice of types of data collected )
- Blockchain often stores more metadata than strictly needed, especially if scores are linked to timestamps, wallet addresses, or other identifiers.
This could conflict with GDPR’s purpose limitation and data minimization principles.
- You must obtain explicit consent before storing such data on-chain. (since this module states using a testing blockchain , this may minimize requirements)
- loosing speed and potentailly space required for data collection can cause issues.

***this is incredibly light and bias, please prove me wrong i can not find anything that coudnt be resolved with the use of other modules, this is not so mainstream in gaming***
#### value of this module 
- cool factor, being able to show off blockchain understanding (decentralized tech.)
- You could auto-calculate rankings or trigger “winner” announcements.
- Once scores are stored, no one can secretly change them.
- Every score is recorded on a public ledger, visible to all participants. (how this might be helpful for tracking progress but im not convinced)
- Tamper resitence , block chains provide immutable data without concensus

if we want to consider the option later, code must be kept modular, all score logic as seperate as possible. 
