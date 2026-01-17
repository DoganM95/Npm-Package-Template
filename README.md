# Intro

Derive javascript projects from this template, that get published as npm packages automatically by github actions. Each push triggers a bump in patch digit of (semantic) version, e.g. `1.0.X`. Minor & Major version bumps have to be done manually. This template and actions use best practices [docs.github.com/en/packages](https://docs.github.com/en/packages/working-with-a-github-packages-registry/working-with-the-npm-registry) to ensure security & convenience, by using the implicit github secret of a repository.

# Features

- Initial push creates an npm packages with version 1.0.0
- Subsequent pushes increase the patch version 1.0.X by 1 each time
- Major `X.0.0` & Minor `0.X.0` versions are up to you
- Repository name is turned into lowercase and taken as the npm package name
- Publishes the NPM package into you github repository
- Chages to `Readme.md` do not trigger a version bump
- Allows version pinning and usage of `@latest`

# Setup

- Derive a repo using this template
- Change Workflow permissions to `Read and write permissions` in Settings -> Actions -> General -> Workflow permissions
- Update the package.json to fit your project
- Set package.json version to 1.0.0 initially
- Push your first commit & see the created npm package

# Notes

## Private Packages

If a private repository is derived from the template, the package also stays private & need authentication to install the npm package. For this, an `.npmrc`  needs to be created at the root of your repository, containing:

```
@YourUserName:registry=https://npm.pkg.github.com/
//npm.pkg.github.com/:_authToken=ghp_...
```

The `authToken` needs to be created on github and needs the rights to read packages to work, npm packages will install perfectly afterwards, like:

```
npm install @doganm95/npm-package-template
```

Make sure, your .npmrc is in the `.gitignore` and never published.

# Usage

The easiest way to create a usable module is creating a class, adding constructors & methods, so it can be instantiated by a user.  
To use the module itself works like this:

```js
const ExampleClass = require("@doganm95/npm-package-template")

const instance = new ExampleClass("User");

console.log("Hello" + instance.getUserName())
```
