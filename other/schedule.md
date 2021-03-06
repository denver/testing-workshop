# Schedule

Just something to help me make sure that I cover everything I want to in the right order.

## Getting Started

- Introductions
  - Setup expectations
  - Go over `workshop-info.md`

### The most basic test

> This is just a hook because people are going to go for a while without touching
> the keyboard and that can be frustrating, so we'll start out with something
> pretty simple.

- Open `other/start.html` in the browser. There's a bug in `addInputValues`.
- Reproduce the bug manually.
- Reproduce the bug by calling `addInputValues`
- Write a simple test that throws an error if the result is not what's expected
- Fix the bug.

**Takeaways**:
- Tests are simply code that runs other code and performs "assertions"
- Testing frameworks abstract this away for us to be more productive in writing tests.

### Why Test

Talk about why testing is important

**Takeaways**:
- Help prevent bugs
- Improve code quality
- Improve development speed

### Introduce the application

Run the application with: `npm start dev`

### Introduce Jest

- Setting up Jest

**New Terms**:
- Assertion: A way for you to specify how things should be. Will throw an error if they are not that way, this is what fails the test.
- Code Coverage: A mechanism for us to understand how much of our code is run during the unit tests. 100% for libs, 75%ish for applications.

**Takeaways**:
- Dependencies: `jest`, `babel-core`, `babel-preset-env`
- Get code coverage with: `jest --coverage`
- Watch mode with: `jest --watch`
- Configure jest with `--config` or `package.json` `jest` property:
  - `"testEnvironment": "jest-environment-node"` if you don't need `jsdom`
  - `collectCoverageFrom` to collect coverage numbers on your whole codebase
  - `coverageThresholds` to keep your coverage from falling

## TAKE A BREAK!

## API Unit Testing

### On existing code

#### `make-me-a-sandwich` Demo

- Run `npm start api.demo.unit`

**Takeaways**:
- Interact with the unit in the same way you would in the actual code. Then
  assert on the resulting value or changes in state.
- Pure functions === easiest to test: compose your application of these as much
  as possible
- Test for use cases rather than for code coverage
- "Object Mother" or "Test DSLs" are really handy (when kept simple).
- Using variables to be explicit about relationships is useful (when kept simple).

#### `get-token-from-header` Exercise

- Run `npm start api.unit`

**Make sure they know**:
- What `req` is and what `req.headers.authorization` looks like.
- `test.skip` -> `test`

### Test Driven Development

#### `sum` Demo

- Run `npm start api.demo.unit`

**Takeaways**:
- Red -> Green -> Refactor
- Write as little as possible before testing again
- Don't forget the refactor step!
- Hard to do for UI or APIs of which you're unclear. Can help to write code
  first, throw away the implementation, and redo with with TDD when you know
  what you want it to look like.
- Feels slower sometimes, but pays big dividends in the long run.
- Easier to do with Unit tests than E2E or integration tests.

#### `arrayify` Exercise

- Run `npm start api.unit`

### Fixing Bugs

#### `get-age` Demo

- Run `npm start api.demo.unit`

**Takeaways**:
- It's similar to TDD, just on pre-existing code.
  (Red -> Green -> Refactor still applies here)
- It's fine to reproduce the bug manually first so you can determine where the bug is (and where to reproduce it).
- Can be done with E2E, Integration, or Unit tests.

#### `user` Exercise

- Run `npm start api.unit`
- Bug is in `api/src/models/user`
- Test is in `api/src/models/__tests__/user`

## TAKE A BREAK!

## API Integration Testing

### `users` Demo

- Run `npm start api.demo.integration`

**Takeaways**:
- The shape of a test:
  Setup State -> Perform Action -> Assert on Resulting State -> Cleanup State
- `before/afterAll/Each` are appropriate for common setup/teardown, but avoid
  using it for creating test data (use a Test DSL). Try to encapsulate cleanup
  in the same place you make the mess in the first place.
- Just like with Unit tests, you interact with the API just like you would if
  you were consuming it in normal code, then assert on the resulting state.
- Occasionally, the only way to assert on the resulting state is to re-query the
  API to find the resulting state. Could also check the database directly...

### `articles` Exercise

- Run `npm start api.integration`

**Make sure they know**:
- Start the mongo server with `npm start mongo`

## Client Unit Testing

###