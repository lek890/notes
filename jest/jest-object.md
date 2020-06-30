##The Jest Object

1. jest.disableAutomock() After this method is called, all require()s will return the real versions of each module (rather than a mocked version).

2. jest.enableAutomock() Enables automatic mocking in the module loader.

3. jest.genMockFromModule(moduleName)

```
const utils = jest.genMockFromModule('../utils').default;
utils.isAuthorized = jest.fn(secret => secret === 'not wizard');

test('implementation created by jest.genMockFromModule', () => {
  expect(utils.authorize.mock).toBeTruthy();
  expect(utils.isAuthorized('not wizard')).toEqual(true);
});
`
``
4. jest.mock(moduleName, factory, options)

5. jest.unmock(moduleName)

6. jest.doMock(moduleName, factory, options)
When using babel-jest, calls to mock will automatically be hoisted to the top of the code block. Use this method if you want to explicitly avoid this behavior.
```

beforeEach(() => {
jest.resetModules();
});

test('moduleName 1', () => {
jest.doMock('../moduleName', () => {
return jest.fn(() => 1);
});
const moduleName = require('../moduleName');
expect(moduleName()).toEqual(1);
});

test('moduleName 2', () => {
jest.doMock('../moduleName', () => {
return jest.fn(() => 2);
});
const moduleName = require('../moduleName');
expect(moduleName()).toEqual(2);
});

```

7. jest.dontMock(moduleName)
When using babel-jest, calls to unmock will automatically be hoisted to the top of the code block. Use this method if you want to explicitly avoid this behavior.

Returns the jest object for chaining.

8. jest.setMock(moduleName, moduleExports) Note: It is recommended to use jest.mock() instead.

9. jest.requireActual(moduleName) Returns the actual module instead of a mock, bypassing all checks on whether the module should receive a mock implementation or not.

10. jest.requireMock(moduleName)

11. jest.resetModules() Resets the module registry - the cache of all required modules. This is useful to isolate modules where local state might conflict between tests.

12. jest.isolateModules(fn)
jest.isolateModules(fn) goes a step further than jest.resetModules() and creates a sandbox registry for the modules that are loaded inside the callback function.

###Jest.spyon

Creates a mock function similar to jest.fn but also tracks calls to object[methodName]. Returns a Jest mock function.

Note: By default, jest.spyOn also calls the spied method. This is different behavior from most other test libraries. If you want to overwrite the original function, you can use jest.spyOn(object, methodName).mockImplementation(() => customImplementation) or object[methodName] = jest.fn(() => customImplementation);

//require actual
// check mock is called in a mock

const mockManualLogin = jest.fn();
jest.mock("./userAuthentication", () => ({
  ...jest.requireActual("./userAuthentication"),
  useUserAuthentication: () => {
    const authenticateAsMoebelUser = mockManualLogin;
    return [authenticateAsMoebelUser];
  }
}));

expect(mockManualLogin).toHaveBeenCalled();

// const MockComponent: React.FC = () => {
//   const { socialLoginSubject$ } = useSocialLogin();
//   useEffect(() => {
//     const test = socialLoginSubject$.subscribe(next => {});
//     return () => {
//       test.unsubscribe();
//     };
//   }, [socialLoginSubject$]);
//   return <div></div>;
// };

jest.mock("@moebel.de/i18n", () => ({
  Translate: function Translate() {
    return <></>;
  },
  useTranslations: () => ""
}));

import { ThemeProviderMock } from "../../../../__mocks__";
```
