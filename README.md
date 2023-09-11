# basic-jest-example

A super minimal example project showing how to setup a JavaScript or TypeScript project for unit testing using Jest.

## Why?

For the curious, here are some reasons why I created this project:

- Finding a simple example project that shows how to setup and use Jest at the most basic level was a challenge.
- I'm not primarily a JavaScript developer so I want to have something that I can reference in the future if need be.
- Again, I'm not primarily a JavaScript developer so creating this project and writing the associated documentation was a good chance to practice and gain a better understanding of JavaScript/TypeScript related tools and project configuration.

## Getting Started

First, choose your path. Sample projects are available for both pure JavaScript or TypeScript implementation. Reference the README for the language of your choice to get started:

- JavaScript - [`javascript/README.md`](javascript/README.md#getting-started)
- TypeScript - [`typescript/README.md`](typescript/README.md#getting-started)

## Noteworthy Items

Mainly for my own future reference, here are some interesting bits I encountered when creating these sample projects:

- The sample apps use the standard naming convention of `__tests__` for the test folder. The name of this folder can be customized using the [`testMatch` Jest configuration option](https://jestjs.io/docs/configuration#testmatch-arraystring).
- The TypeScript version of the project requires some additional files/dependencies:
    - Need for a `jest.config.js/ts` Jest configuration file so that Jest can properly work with TypeScript.
    - Need for the `ts-node` dependency since the Jest configuration file is written in TypeScript (i.e. `jest.config.ts`).
- Adding the "test" script to `package.json` is optional, but seems to be industry standard. Can also run Jest directly using `npm exec jest` or `npx jest`.

## References

- [Jest Getting Started docs](https://jestjs.io/docs/getting-started) - main source of demo code.
- [ts-jest Getting Started docs](https://kulshekhar.github.io/ts-jest/docs/getting-started/installation) - help understanding how to setup the Jest configuration file to work with TypeScript.
- [ChatGPT](https://chat.openai.com) - answering a few JavaScript/TypeScript-related questions to help me quickly get up to speed with the development environment.
