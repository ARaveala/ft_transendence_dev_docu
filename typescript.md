# Typescript 
TypeScript is a typed superset of JavaScript developed by Microsoft. It adds static typing, interfaces, and modern language features to JavaScript,
making it easier to catch errors early and write scalable, maintainable code.
TypeScript code compiles into regular JavaScript, so it runs anywhere JavaScript does — in browsers, Node.js, etc.

#### What it offers
- static typing , detects type errors before runtime, can help prevent bugs in game logic and API calls
- interfaces, defines objects shapes and contracts, ensuring consitent player or match data
- enums, useful for game stats (e.g READY, PLAYING)
- modules, keep frontend/backend clean
- type aliases , create custome types to simplify complex data structures

### Tools with typescript
- npm or pnpm package manager , like apt but for js, pnpm is appartently more superior , it uses symlinks.
- ESLint code linter, like cppcheck or clang-tidy (these can be extensions on vscode they help show code correctness as based on a certain standard).
- Prettier code formatter like clang-format for constinet styling, usefull if multiple people are colaborating in shared scope.
- Husky A tool that runs scripts before you commit code (called Git hooks), this well help enforce rules across the team.
- ts-node allows you to run TypeScript files directly without compiling them first.

#### Common mistakes 
- Using ```any``` too much any tells TypeScript to stop checking your code ,an extension called any-xray can help us find them in code.
- Not writing type hints for functions If you don’t tell TypeScript what types your function takes or returns, it might guess wrong
leading to bugs. It’s safer to write them out.
- Not turning on strict mode, strict mode helps TypeScript catch more mistakes.
- Forgetting to check for null or undefined TypeScript won’t always stop you from using a value that might not exist. Use tools like optional chaining (?.) or default values (??) to stay safe

- <https://www.typescriptlang.org/docs/>
