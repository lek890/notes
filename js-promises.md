**Async/Await**

Async/await is actually just syntax sugar built on top of promises.

**Async**

An async keyword before a function means the function always returns a promise. The values returned are wrapped in the resolve 
automatically.

example

```
async function giveFive() {
  return 5;
}

giveFive().then(alert)

// would alert 5
```

this is same as 


```
async function giveFive(){
  Promise.resolve(5);
}

```

So async ensures that the function returns a promise.


**Await**

Await keyword works only inside an async function.

Keyword `await` makes Javascript wait until the promise the promise that is resolved and returns its result.

for ex:


```
async function giveSeven() {

const aPromiseThatResolvesSoon = new Promise(  (res, rej) => setTimeout( ()  => res('7'), 1000 )  )

const result = await promise;
//q: why the promise doesnt have paranthesis?

alert(result)

}

giveSeven()
```




