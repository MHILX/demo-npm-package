# How to create an NPM package & Test locally using `npm link`

## Step 1: Set up the project structure
Create a new directory for your package and navigate to it in the terminal.

## Step 2: Initialize the project
Run `npm init` to initialize a new _Node.js_ project. Follow the prompts to provide the necessary details.

## Step 3: Install dependencies
Install the required dependencies, including TypeScript and any other packages you may need.

    npm install typescript --save-dev

## Step 4: Set up TypeScript configuration
Create a `tsconfig.json` file in the root of your project with the following configuration:

```json
{
  "compilerOptions": {
    "target": "es6",
    "module": "es6",
    "outDir": "dist",
    "declaration": true,
    "esModuleInterop": true
  },
  "include": ["src"],
  "exclude": ["node_modules"]
}
```

## Step 5: Create the TypeScript source files
Create a _src_ directory in the project root and add your TypeScript source files inside it. Use the ES6 export syntax to export the desired values or functions.

For example, create a file named `greeting.ts` with the following content:

```typescript
export function sayHello(name: string): void {
  console.log(`Hello, ${name}!`);
}
```

## Step 6: Build the project
Run `tsc` to transpile the TypeScript files into JavaScript. The compiled JavaScript files will be placed in the _dist_ directory according to the _outDir_ option in `tsconfig.json`.

    npx tsc

## Step 7: Create the package
Create a `package.json` file in the _dist_ directory with the necessary package details.

```json
{
  "name": "your-package-name",
  "version": "1.0.0",
  "main": "index.js",
  "types": "index.d.ts"
}
```

## Step 8: Create an index file
Create an `index.js` file in the dist directory that imports and re-exports the desired values from your package.

```javascript
const { sayHello } = require("./greeting");

module.exports = {
  sayHello
};
```

## Step 9: Link the package
In the project root, run `npm link` to create a global link to your package.
    
        npm link

## Step 10: Test the package locally
Create a new _test_ directory for testing your package and navigate to it in the terminal. Run `npm link your-package-name` to link your package to the test project.

    npm link your-package-name

Now, you can import and use the exported functions from your package in the consumer project as if it were a regular dependency.

```javascript
const { sayHello } = require("your-package-name");

sayHello("mohammed"); // Output: Hello, mohammed!
```

By following these steps, you can create a Node package using TypeScript with ES6 export syntax and consume it locally using `npm link`.