# Laouni First Angular Project

This project was generated with [Angular CLI](https://github.com/angular/angular-cli) version 6.1.2.

## TL;DR

## Technologies

- 🔥  `react` -  server side and client side view components.
- 🤖  `redux` -  application state and actions provider.
- 🚄  `express` - nodejs server.
- 👮  `hpp`, `helmet` and `content security policy` - nodejs security layer.
- 📦  `webpack` - bundling of both client and server with tree shaking.
- 🚀  `babel` - transpiles ES6+ where needed.
- 🍃  `sass`, `BEM` and `atomic design` - modular styles.
- 🏁  `gridle` - grid system.
- 🔧  `eslint` (airbnb), `stylelint` and `flow` - code quality tools.
- 📕  `documentation` - JSDoc compatible generation tool.
- 📗  `aigis` - styleguide generator.
- 👟  `jest` with snapshots and `istanbul` coverage - testing.
- 😺  `yarn` - dependencies manager.

## Installation

- Clone the repository,
- Install NodeJS LTS (with nvm),
- Install `yarn` (eg . `brew install yarn`),
- Execute `yarn install`.

# Development

- Launch the local controller API with `yarn api:proxy` (with the distant controller api) or `yarn api:mocks`.
- Launch the NodeJS application with `yarn dev`.

## Project tasks (✨ Yarn)

- `yarn generate`- 'component component-name' - Generate a new component. You can also use `yarn generate directive|pipe|service|class|guard|interface|enum|module`.
- `yarn dev`    - Starts the development server. Navigate to `http://localhost:4200/`. The app will automatically reload if you change any of the source files.
- `yarn build`  - Build the sources (webpack) to client and server files.
- `yarn start`  - Starts the built server (works only after a build).
- `yarn analyze`- Check the client bundles, use it to find wrong imported deps.
- `yarn test`   - Executes all the test suite (flow checking, unit tests and linters).
- `yarn lint`   - Check the code quality with ESLint and Stylelint.
- `yarn jest`   - Launch the unit tests and generates a coverage report.
- `yarn e2e`    - Execute the end-to-end tests via [Protractor](http://www.protractortest.org/).
- `yarn metadata:phones` - Will update the metadata json for validating the phone numbers.

## Build

Run `ng build` to build the project. The build artifacts will be stored in the `dist/` directory. Use the `--prod` flag for a production build.

## Unit Tests

[View Unit Tests section](tools/docs/unit-tests.md)

## Js best practices

[View Js best practices section](tools/docs/js-tech.md)

## CSS/SASS & Icons

[View CSS/SASS & Icons section](tools/docs/styles.md)

## Tracking

[View Tracking section](tools/docs/tracking.md)

## Git

- Feature branches should be named as `feat/ONE-4445`.
- Don't commit directly to `develop` branch. Always use a Merge request with your feature branch.

Commit messages should be as :

```
<type>(<scope>#ANGULAR-XX): <subject>
```

eg.

```
feat(CFG#ANGULAR-01): add video list
```

With **type** :

* **feat**: A new feature,
* **fix**: A bug fix,
* **docs**: Documentation only changes,
* **style**: Changes that do not affect the meaning of the code (white-space, formatting, missing semi-colons, etc),
* **refactor**: A code change that neither fixes a bug nor adds a feature,
* **perf**: A code change that improves performance,
* **test**: Adding missing tests,
* **chore**: Changes to the build process or auxiliary tools and libraries such as documentation generation.

With **scope** :

* **CFG**: CONFIG

## Project Structure

```
/
|- config // Each client configuration as JSON (node-config)
|
|- mocks // Development mocks (Exposed by express during development only)
|
|- build // The target output dir for our build commands
|  |- client // The built client module
|  |- server // The built server module
|
|- src  // All the source code
|  |- server // The server bundle entry and specific source
|  |- client // The client bundle entry and specific source
|  |- shared // The shared code between the bundles)
|       |- components // Most of the project components
|              |- atoms // Atomic components (like input)
|              |- cms // Registry (only registry)
|              |- commons // Historical (don't add component here)
|              |- molecules // Group of atomic components, used across multiples slides
|              |- slides // Slides components (view Glossary)
|       |- constants // constant files
|       |- containers
|       |- hoc
|       |- middlewares
|       |- redux // redux
|       |- styleguide // can be viewed on styleguide.html (renault uci or dacia vn)
|       |- utils
|- tools
|  |- development // Tool for hot reloading development
|  |
|  |- webpack
|     |- client.config.js // Client webpack configuration
|     |- server.config.js // Server webpack configuration
|     |- configFactory.js // Webpack configuration builder
|     |- configFactory.dev.js // Webpack configuration builder (local hot-reload)
```

## Overview

This project uses Webpack 2 to produce bundles for both the client and the
server. You will notice the following Webpack configuration files:

   - `tools/webpack/client.config.js`
   - `tools/webpack/server.config.js`

During development, you can use the website into one client/brand context (Renault, Dacia, ...). The `developmentBrand` can be define into the config files.

For a production build, webpack will produce a client build for each client defined into the `brands` array from the config files. It generates a single server file.

Using Webpack and babel across all of our source allows us to use the same level of javascript (e.g. es2015/2016/2017) without having to worry about what each target environment supports.  In addition to this it allows our client/server code to both support the additional file types that a typical React application may import (e.g. CSS/Images).

## Express Server Security

We make use of the `helmet` and `hpp` middleware libraries to provide a fairly advanced security configuration for our express server, attempting to follow best practices. If you are unfamiliar with CSPs then I highly recommend that you do some reading on the subject:

  - https://content-security-policy.com/
  - https://developers.google.com/web/fundamentals/security/csp/
  - https://developer.mozilla.org/en/docs/Web/Security/CSP
  - https://helmetjs.github.io/docs/csp/

If you are relying on scripts/styles/assets from CDN or from any other server/application that is not hosted on the same URL as your application then you will need to explicitly add the respective CSN/Server URLs to the Content Security Policy within the express configuration.  For example you can see I have had to add the polyfill.io CDN in order to allow us to use the polyfill script.

You may find CSPs annoying at first, but it is a great habit to build. The CSP configuration is an optional item for helmet, however you should not remove it without making a serious consideration that you do not require the added security.


## Project Dependencies

The dependencies within `package.json` are structured so that the libraries required to transpile/bundle the source are contained within the `devDependencies` section, whilst the libraries required during the server runtime are contained within the `dependencies` section.

## Further help

To get more help on the Angular CLI use `ng help` or go check out the [Angular CLI README](https://github.com/angular/angular-cli/blob/master/README.md).
