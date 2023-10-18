# MHILX NPM Package

## Install Package
    npm install @mhilx/greeting --registry=https://npm.pkg.github.com

## Usage Example
```TypeScript
import sayHello from "@mhilx/greeting";
console.log(sayHello("World"));
```
---
## How to publish a package to GitHub Packages

### Initialize NPM in your project
    npm init -y

This command will create a `package.json` file. 

### Create a personal access token
To publish your npm package using a GitHub token, you need to select the appropriate scopes when creating the token. The scopes determine the permissions and access levels that the token will have. Here are the recommended scopes for publishing an npm package:

  1. repo: This scope is required to access the repository where your npm package is located. It allows the token to read and write repository-related information.

  2. write:packages: This scope is required to publish packages to the GitHub Packages registry. It allows the token to publish, update, and delete packages associated with the repository.

  3. read:packages: This scope is required to install packages from the GitHub Packages registry. It allows the token to read and download packages associated with the repository.

  4. delete:packages: This scope is optional but recommended if you want to have the ability to delete packages from the GitHub Packages registry using the token.

When creating your GitHub token, make sure to select these scopes to ensure that you have the necessary permissions to publish your npm package.

### Create `.npmrc` file at root of project and the following lines
    @NAMESPACE:registry=https://npm.pkg.github.com
    //npm.pkg.github.com/:_authToken=<YOUR_TOKEN>

### Publish Package
    npm publish --access=public