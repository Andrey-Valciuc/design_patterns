# The Revealing Module Pattern

The Revealing Module pattern is a pattern used to encapsulate some private logic and then expose a public API.

Usually it is expressed via ana **Immediately Invoked Function Expression (IIFE)** that returns an object literal containing the public methods and properties:

```javascript
const myModule = (() => {
  const privateFoo = 1;
  const privateBaz = 2;
  // (Private Initialization Logic goes here)
  return {
    publicFoo() {},
    publicBaz() {},
  };
})();
```

Any functions returned by the IIFE will form a closure around their respective scopes,
meaning that they will continue to have access to the private scope.
