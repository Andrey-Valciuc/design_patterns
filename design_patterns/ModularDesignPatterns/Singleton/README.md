# Singleton Class Pattern

It may not always be the case that your class will need to be utilized as a conventionally OOP class with inheritance and
instantiation. For example, we may wish to set up a utility object with a class definition so that we can define any initialization logic within the constructor and provide a semblance of encapsulation within its methods:

```javascript
const utils = new (class {
  constructor() {
    this.#privateThing = 123;
    // Other initialization logic here...
  }
  utilityA() {}
  utilityB() {}
  utilityC() {}
})();
utils.utilityA();
```

Here the class is created and immediately instantiated.

Singletons are useful when only one instance of a class is required. The singular instance
produced is similar in nature to the Conventional or Revealing Module pattern. It enables
you to wrap up an abstraction with the option of private variables and implicit construction
logic. Common use cases of singletons include Utilities, Logging, Caching, Global Event Buses,
and so on.
