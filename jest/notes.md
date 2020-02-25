
- dom testing
- snapshot testing

###Expect:
- expect.extend - to add new functionality to expect 
- expect.anything - to check a func is called without a non null argument
- expect.any(constructor) - expect(mock).toBeCalledWith(expect.any(Number));
- expect.arrayContaining - expect(['Alice', 'Bob', 'Eve']).toEqual(expect.arrayContaining(['Alice', 'Bob']);
- expect.assertions(number) - expect.assertions(2); - to ensure how manu assertions are called
- expect.hasAssertions() - verifies atleast one assertion is called during the test
- expect.not.arrayContaining(array) - expected not a subset of received
- expect.not.objectContaining(object) - expect not a subset of received - expect({bar: 'baz'}).toEqual(expect.not.objectContaining(expected));
- expect.not.stringContaining(string) - same as above. expect('Hello world').toEqual(expect.not.stringContaining('how are you?'))
- expect.stringMatching(string | regex) - expect.arrayContaining(expect.stringMatching(/Âlic/))
- .not
- .resolves
```
test('', () => {
   //return is important
   return expect(Promise.resolve('lemon')).resolves.toBe('lemon')
})
```
- .rejects - complementary to above
- .toBe
- .toHaveBeenCalled - alias toBeCalled
- .toHaveBeenCalledTimes
- .toHaveBeenCalledWith
- .toHaveBeenLastCalledWith
- .toHaveBeenNthCalledWith
- .toHaveReturned() alias toReturn()  to test that the mock function successfully returned (i.e., did not throw an error) at least one time.
- .toHaveReturnedTimes(number)
- .toHaveReturnedWith(value)
- .toHaveLastReturnedWith
- .toHaveNthReturnedWith
- .toHaveLength
- .toHaveProperty(keypath, value)
- .toBeCloseTo - for comparing floating numbers
- .toBeDefined - to check variable is defined
- .toBeFalsy 
- .toBeGreaterThan
- .toBeGreaterThanOrEqual
- .toBeLessThan
- .toBELessThanOrEqual\
- .toBeInstanceOf
- .toBeNull
- .toBeTruthy
- .toBeUndefined
- .toBeNan
- .toContain //check item is in array
- .toContainEqual //to check array has an item of specific shape
- .toEqual
- .toMatch - string matches a regular exp
- .toMatchObject - to check an object matches a subset of the properties
- .toMatchSnapshot
- .toMatchInlineSnapshot
- .toStrictEqual - to check objects has same structute and types
- .toThrow
- .toThrowErrorMatchingSnapshot
- .toThrowErrorMatchingInlineSnapshot

when to call resetMocks?
