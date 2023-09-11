# Basic Jest Example - JavaScript

A super simple example project showing how to unit test JavaScript using [Jest](https://jestjs.io).

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

This will install the only dependency (technically just a dev dependency), which is Jest.

### 3. Running the Tests

Run the tests using `npm`:

```Shell
npm test
```

## Project Structure

The following files make up this project:

* `package.json` - Standard npm JavaScript app metadata. Defines the `test` script and `jest` as a development dependency.
* `package-lock.json` - Standard auto-generated npm JavaScript app lockfile. Defines the dependency versions currently in use.
* `src/sum.js` - The main application code. A simple `sum()` function that adds 2 numbers together.
* `__tests__/sum.test.js` - The main test code. Defines a single test for the `sum()` function.

## How This Project Was Created

### 1. Create basic directory structure.

1. Create tests folder:

```Shell
mkdir __tests__
```

2. Create initial test file:

```Shell
touch __tests__/sum.test.js
```

3. Create source folder:

```Shell
mkdir src
```

4. Create initial source file:

```Shell
touch src/sum.js
```

### 2. Add source code.

1. Create `sum()` function in `src/sum.js`:

```JavaScript
function sum(a, b) {
    return a + b;
}

module.exports = sum;
```

2. Create test for `sum()` function in `__tests__/sum.test.js`:

```JavaScript
const sum = require('../src/sum');

test('adds 1 + 2 to equal 3', () => {
    expect(sum(1, 2)).toBe(3);
});
```

### 3. Setup dependencies.

Install Jest using the `--save-dev` flag to define it as a development dependency in `package.json`:

```Shell
npm install --save-dev jest
```

### 4. Finish setting up `package.json`.

Define a `test` script that runs `jest`:

```JSON
{
  "scripts": {
    "test": "jest"
  },
  "devDependencies": {
    "jest": "^29.5.0"
  }
}
```

### 5. Run tests

Run the tests to verify everything was setup correctly:

```Shell
npm test
```
