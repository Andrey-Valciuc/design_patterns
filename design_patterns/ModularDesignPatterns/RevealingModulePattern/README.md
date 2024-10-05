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

An example of a real-world Revealing Module would be this simple DOM Component that
contains logic for rendering a notification to users:

```javascript
const notification = (() => {
  const d = document;
  const container = d.body.appendChild(d.createElement("div"));
  const message = container.appendChild(d.createElement("p"));
  const dismissBtn = container.appendChild(d.createElement("button"));
  container.className = "notification";
  dismissBtn.textContent = "Dismiss!";
  dismissBtn.onclick = () => {
    container.style.display = "none";
  };
  return {
    display(msg) {
      message.textContent = msg;
      container.style.display = "block";
    },
  };
})();
```

The notification variable in the outer scope will refer to the object returned by the IIFE,
meaning we have access to its public API:

```javascript
notification.display("Hello user! Something happened!");
```
