# Conventional Model Pattern

The Conventional Module pattern is usually expressed as a plain object literal with a set of methods:

```javascript
const timeDiffUtility = {
  minutesBetween(dateA, dateB) {},
  hoursBetween(dateA, dataB) {},
  daysBetween(dateA, dateB) {},
};
```

Also we may want to provide methods that change the state or configuration of the entire module (such as **setConfig**):

```javascript
const timeDiffUtility = {
  setConfig(config) {
    this.config = config;
  },
  minutesBetween(dateA, dateB) {},
  hoursBetween(dateA, dataB) {},
  daysBetween(dateA, dateB) {},
};
```

The Conventional Module pattern is incredibly flexible since it is just a plain object. You can easily compose the objects of methods from functions defined elsewhere, as well.

The Conventional Module pattern is useful in any scenario where you simply wish to wrap a set up a set of related methods or properties into something with a common name such as logging utilities:

```javascript
const logger = {
  log(message) {
    /* ... */
  },
  warn(message) {
    /* ... */
  },
  error(message) {
    /* ... */
  },
};
```
