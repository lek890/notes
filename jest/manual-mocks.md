Manual mocks

Mocking user modules

modules
  __mocks__
     user.js
  user.js

When requiring that module in the tests, explicity calling
```
jest.mock('./moduleName')
```
is required.

Mocking node modules 

- keep the __mocks__ adjacent to the node_modules
- explicity mocking the module in the test as above is not required.

when automock is set to true, the manual mock implementation will be used instead of the automatically created mock, even if jest.mock('moduleName') is not called. To opt out of this behavior you will need to explicitly call jest.unmock('moduleName') in tests that should use the actual module implementation.

Mocking methods which are not implemented in JSDOM

workaround - 

```
Object.defineProperty(window, 'matchMedia', {
  writable: true,
  value: jest.fn().mockImplementation(query => ({
    matches: false,
    media: query,
    onchange: null,
    addListener: jest.fn(), // deprecated
    removeListener: jest.fn(), // deprecated
    addEventListener: jest.fn(),
    removeEventListener: jest.fn(),
    dispatchEvent: jest.fn(),
  })),
});
```
