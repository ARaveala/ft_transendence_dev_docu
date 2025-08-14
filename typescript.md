# Typescript 
TypeScript is an extension of JavaScript that was created by Microsoft. Think of it like modern C++ is to C: it adds powerful features on top of a foundational language to make it safer and more robust.

The most important thing TypeScript adds is static typing. This means you can declare the type of a variable, function parameter, or return value, just like you would in C++. The TypeScript compiler then checks your code for type errors before you run it, which helps you catch a lot of bugs early. Your TypeScript code is ultimately "compiled" into regular JavaScript, so it can run anywhere JavaScript does (in a web browser, on a server with Node.js, etc.).

## Key Features of TypeScript
Here are some of the most helpful features TypeScript offers, with their C/C++ parallels:

- Static Typing: Just like in C++, you can declare variables with a specific type (string, number, boolean). This is a massive help because the compiler will warn you if you try to do something like add a string to a number, which can be a common source of bugs in JavaScript.
- Interfaces: Interfaces are similar to C++ abstract classes or structs. They define the "shape" of an object. You can use an interface to guarantee that a player object, for example, will always have a username (string) and a score (number). This creates a contract that your code must follow, ensuring consistent data.
- Enums: You can use enums to define a set of named constants, just like in C++. They are perfect for representing game states (e.g., GameStatus.READY, GameStatus.PLAYING) or other fixed values in your code.
- Modules: Modules are similar to C++ header files and source files. They allow you to organize your code into separate files and explicitly import and export what you need. This keeps your code clean and avoids naming conflicts.
- Type Aliases: You can use type aliases to give a new name to a complex data structure. This is like a C++ typedef. It simplifies your code and makes it more readable.

## Essential Tools for TypeScript
The following tools will help you work with TypeScript effectively. Many have direct parallels to tools you're already familiar with.

- npm or pnpm (Package Manager): This is like apt or brew for JavaScript. It's how you install third-party libraries and tools for your project. pnpm is often considered superior because it uses symlinks, which saves disk space.
- ESLint (Code Linter): This tool is just like cppcheck or clang-tidy. It analyzes your code for potential errors and stylistic issues, helping you maintain a consistent and high-quality codebase. Many editors, like VS Code, integrate with ESLint to show you warnings and errors as you type.
- Prettier (Code Formatter): This is the equivalent of clang-format. It automatically formats your code to a consistent style, which is especially useful when multiple people are collaborating on the same project.
- Husky (Git Hooks): This tool runs scripts automatically before you commit your code to Git. You can use it to ensure that every team member formats their code with Prettier and checks for linting errors before pushing changes, helping to enforce team rules.
- ts-node: This tool allows you to run a TypeScript file directly without having to first compile it into JavaScript. It's incredibly useful for quick testing and running scripts during development.

## Common Beginner Mistakes
Avoiding these common pitfalls will help you write better TypeScript code from the start:

- Using any too much: The any type tells TypeScript to stop checking your code, effectively turning off the main benefit of the language. This can hide bugs. It's better to find the correct type or create one yourself. A tool like any-xray can help you find and fix any types in your code.
- Not writing type hints for functions: Just like in C++, if you don't declare the types for your function parameters and return values, TypeScript might have to guess them. It's much safer and more reliable to be explicit.
- Not turning on strict mode: In your TypeScript configuration file (tsconfig.json), enabling strict mode ```("strict": true)``` helps the compiler catch more potential mistakes. It's a best practice for any new project.
- Forgetting to check for null or undefined: TypeScript won't always save you from using a variable that might not have a value. A common mistake is trying to access a property on an object that is null or undefined, which will cause your program to crash. You can avoid this with safe access operators:
- Optional Chaining (?.): This is a safe way to access nested properties without a long chain of if statements. If a property in the chain is null or undefined, the expression will immediately stop and return undefined instead of throwing an error.

```
// Old way, prone to errors:
// const playerName = player.profile.name; // Throws error if player or profile is null

// Safe way with optional chaining:
const playerName = player?.profile?.name; // Returns undefined if player or profile is null/undefined
```

- Nullish Coalescing (??): This operator allows you to provide a default value when a variable is strictly null or undefined. It's a safer alternative to the logical OR (||) operator, which can give unexpected results if a value is 0 or an empty string.

```
// Old way, with a potential bug:
// const score = player.score || 0; // If player.score is 0, it incorrectly returns 0

// Safe way with nullish coalescing:
const score = player.score ?? 0; // If player.score is null/undefined, it defaults to 0
```

<https://www.typescriptlang.org/docs/>
