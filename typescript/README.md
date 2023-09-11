# Basic Jest Example - TypeScript

A super simple example project showing how to unit test TypeScript using [Jest](https://jestjs.io).

## Getting Started

If you're not a web developer, look for best practices on how to install the prerequisites for your development environment.

Once the prerequisites are installed, you can proceed to installing the project dependencies and running the tests.

### 1. Installing Prerequisites

Install [Node.js](https://nodejs.org/en), ideally through a version manager like [nvm](https://github.com/nvm-sh/nvm).

### 2. Installing Project Dependencies

Open a terminal to this directory, then install the project dependencies using:

```Shell
npm install
```

This will install the project dependencies, which are mainly Jest, TypeScript, and supporting libraries.

### 3. Running the Tests

Run the tests using `npm`:

```Shell
npm test
```

## Project Structure

The following files make up this project:

* `package.json` - Standard npm JavaScript app metadata. Defines the `test` script as well as Jest and TypeScript related development dependencies.
* `package-lock.json` - Standard auto-generated npm JavaScript app lockfile. Defines the dependency versions currently in use.
* `jest.config.ts` - Jest configuration file that allows Jest to understand TypeScript.
* `src/sum.ts` - The main application code. A simple `sum()` function that adds 2 numbers together.
* `__tests__/sum.test.ts` - The main test code. Defines a single test for the `sum()` function.

### Jest Configuration File

In order for Jest to understand TypeScript, a Jest configuration file must be created. This file can be created using JavaScript as `jest.config.js` or TypeScript as `jest.config.ts`. If using the TypeScript version of the configuration file, then an additional `ts-node` development dependency must be defined in `package.json`.

If don't have the configuration file setup properly, then you will get a "Jest encountered an unexpected token" error like the following when running `npm test`:

```text
> test
> jest

 FAIL  __tests__/sum.test.ts
  ● Test suite failed to run

    Jest encountered an unexpected token

    Jest failed to parse a file. This happens e.g. when your code or its dependencies use non-standard JavaScript syntax, or when Jest is not configured to support such syntax.

    Out of the box Jest supports Babel, which will be used to transform your files into valid JS based on your Babel configuration.

    By default "node_modules" folder is ignored by transformers.

    Here's what you can do:
     • If you are trying to use ECMAScript Modules, see https://jestjs.io/docs/ecmascript-modules for how to enable it.
     • If you are trying to use TypeScript, see https://jestjs.io/docs/getting-started#using-typescript
     • To have some of your "node_modules" files transformed, you can specify a custom "transformIgnorePatterns" in your config.
     • If you need a custom transformation specify a "transform" option in your config.
     • If you simply want to mock your non-JS modules (e.g. binary assets) you can stub them out with the "moduleNameMapper" config option.

    You'll find more details and examples of these config options in the docs:
    https://jestjs.io/docs/configuration
    For information about custom transformations, see:
    https://jestjs.io/docs/code-transformation

    Details:

    /Users/username/Repositories/basic-jest-example/typescript/__tests__/sum.test.ts:1
    ({"Object.<anonymous>":function(module,exports,require,__dirname,__filename,jest){import sum from '../src/sum';
                                                                                      ^^^^^^

    SyntaxError: Cannot use import statement outside a module

      at Runtime.createScriptFromCode (node_modules/jest-runtime/build/index.js:1495:14)

Test Suites: 1 failed, 1 total
Tests:       0 total
Snapshots:   0 total
Time:        0.168 s
Ran all test suites.
```

See below for more information about the contents that make up the Jest configuration file.

## How This Project Was Created

### 1. Create basic directory structure.

1. Create tests folder:

```Shell
mkdir __tests__
```

2. Create initial test file:

```Shell
touch __tests__/sum.test.ts
```

3. Create source folder:

```Shell
mkdir src
```

4. Create initial source file:

```Shell
touch src/sum.ts
```

### 2. Add source code.

1. Create `sum()` function in `src/sum.ts`:

```TypeScript
function sum(a: number, b: number): number {
    return a + b;
}

export default sum;
```

2. Create test for `sum()` function in `__tests__/sum.test.ts`:

```TypeScript
import sum from '../src/sum';

describe('sum module', () => {
    test('adds 1 + 2 to equal 3', () => {
        expect(sum(1, 2)).toBe(3);
    });
});
```

### 3. Setup dependencies.

1. Install Jest using the `--save-dev` flag to define it as a development dependency in `package.json`:

```Shell
npm install --save-dev jest
```

2. Install TypeScript since we want to use it instead of vanilla JavaScript:

```Shell
npm install --save-dev typescript
```

3. Install the Jest types package to allow the Jest global APIs to be typed for test files written in TypeScript:

```Shell
npm install --save-dev @types/jest
```

**NOTE:** As an alternative to the `@types/jest` package, you can use the `@jest/globals` package with some additional import statements in tests. See the [Jest docs](https://jestjs.io/docs/getting-started#type-definitions) for more info.

4. Install `ts-jest` to allow Jest to transpile TypeScript:

```Shell
npm install --save-dev ts-jest
```

**NOTE:** Using `ts-jest` also requires setup of a Jest configuration file (e.g. `jest.config.js/ts`) to inform Jest how to handle `.ts` files correctly. See [ts-jest docs](https://kulshekhar.github.io/ts-jest/docs/getting-started/installation/#jest-config-file) for more info.

5. Install `ts-node` to allow Jest to compile the Jest configuration file written in TypeScript:

```Shell
npm install --save-dev ts-node
```

**NOTE:** Installing the `ts-node` package is **not** required if using a **JavaScript** Jest config file (e.g. `jest.config.js`). The `ts-node` package is only required if using a **TypeScript** Jest configuration file (e.g. `jest.config.ts`). When using `TypeScript`, Jest uses `ts-node` to compile the config file. See [Configuring Jest docs](https://jestjs.io/docs/configuration) for more info.

### 4. Finish setting up `package.json`.

Define a `test` script that runs `jest`:

```JSON
{
  "scripts": {
    "test": "jest"
  },
  "devDependencies": {
    "@types/jest": "^29.5.1",
    "jest": "^29.5.0",
    "ts-jest": "^29.1.0",
    "ts-node": "^10.9.1",
    "typescript": "^5.0.4"
  }
}
```

**NOTE:** As mentioned above, you will likely not have the `ts-node` package defined in your `package.json` if using a JavaScript Jest configuration file (i.e. `jest.config.js`).

### 5. Setup Jest config

As mentioned above, the Jest configuration file can be written in either JavaScript or TypeScript. Since the rest of this sample project is using TypeScript, I opted for Option 2 below to also create the configuration file in TypeScript.

#### Option 1 - Create JavaScript Jest config file

Use `ts-jest` to create a basic `jest.config.js` Jest configuration file in JavaScript:

```Shell
npx ts-jest config:init
```

The contents of the generated `jest.config.js` file should look something like the following:

```JavaScript
/** @type {import('ts-jest').JestConfigWithTsJest} */
module.exports = {
  preset: 'ts-jest',
  testEnvironment: 'node',
};
```

#### Option 2 - Create TypeScript Jest config file

Copy one of the TypeScript Jest config examples from the [Jest docs](https://jestjs.io/docs/configuration). I chose the one that exports a function returning a `Config` object. Make sure to manually add the `preset: 'js-test'` and `testEnvironment: node` values as well.

Once complete, the contents of `jest.config.ts` should look something like the following:

```TypeScript
import type { Config } from 'jest';

export default async (): Promise<Config> => {
  return {
    preset: 'ts-jest',
    testEnvironment: 'node',
    verbose: true,
  };
};
```

**NOTE:** Technically the `testEnvironment: 'node'` isn't necessary as `"node"` is the [Jest default](https://jestjs.io/docs/configuration#testenvironment-string). Likewise, the `verbose: true` isn't strictly necessary, but can be useful when debugging setup issues.

### 6. Run tests

Run the tests to verify everything was setup correctly:

```Shell
npm test
```
