Mock Functions

- mockFn.mock.calls - array of call arguments
- mockFn.mock.results - array of result of calls 
```
[
  {
    type: 'return',
    value: 'result1',
  },
  {
    type: 'throw',
    value: {
      /* Error instance */
    },
  },
  {
    type: 'return',
    value: 'result2',
  },
];

`
``

- mockFn.mock.instances = array of object instances instantiated from the mock function
- mockFn.mockClear() - clear all info in mock.calls and mock.instances
- mockFn.mockReset() - mockClear() + resets returns values and implementations
- mockFn.mockRestore() - mockReset() + restores original implementation
Beware that mockFn.mockRestore only works when the mock was created with jest.spyOn. Thus you have to take care of restoration yourself when manually assigning jest.fn().

- mockFn.mockImplementation(fn)
```
module.exports = class SomeClass {
   m(a, b) {}
}


//test
jest.mock('./SomeClass');
const mMock = jest.fn();

SomeClass.mockImplementation(() => ({
return {
m : mMock
}

}));


const some = new SomeClass();
some.m('a', 'b')
console.log('Calls to m: ', mMock.mock.calls);


```

- mockFn.mockImplementationOnce(fn)

```

const myMockFn = jest
  .fn(() => 'default')
  .mockImplementationOnce(() => 'first call')
  .mockImplementationOnce(() => 'second call');

// 'first call', 'second call', 'default', 'default'
console.log(myMockFn(), myMockFn(), myMockFn(), myMockFn());
```

- mockFn.mockName(value)
- mockFn.mockReturnThis() //return this
- mockFn.mockReturnValue(value)
- mockFn.mockReturnValueOnce(value) //same logic as mockImplementationOnce
- mockFn.mockResolvedValue(value)
- mockFn.mockResolvedValueOnce(value)
- mockFn.mockRejectedValue(value)
- mockFn.mockRejectedValueOnce(value)
