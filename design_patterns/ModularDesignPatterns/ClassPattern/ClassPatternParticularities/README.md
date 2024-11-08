# Class Pattern Particularites

## Static Methods

Static methods and properties can be declared by using the static keyword:

```javascript
class Accounts {
  static allAccounts = [];
  static tallyAllAccounts() {
    // ...
  }
}
Accounts.tallyAllAccounts();
Accounts.allAccounts; // => []
```

Static methods are useful when you have a method or property whose functionality and
existence are semantically related to the entire class as opposed to a singular instance.

## Public and private fields

To declare a public field (that is, a property) on your instance, you can simply declare this
within the class definition syntax in line:

```javascript
class Rectangle {
  width = 100;
  height = 100;
}
```

These fields are initialized for each instance and are, therefore, mutable on the instance
itself. You can also define private fields by prefixing their identifier with a # symbol:

```javascript
class Rectangle {
  #width = 100;
  #height = 100;
  constructor(width, height) {
    if (width && !isNaN(width)) {
      this.#width = width;
    }
    if (height && !isNaN(height)) {
      this.#height = height;
    }
  }
}
```

Private fields are only accessible by the class itself. Sub-classes do not have access.

## Extending classes

Inheritance within the Class pattern can very simply be achieved by using the class ...
extends syntax like so:

```javascript
class Animal {}
class Tiger extends Animal {}
```

This will ensure that any instance of Tiger will have [[Prototype]], which itself has
[[Prototype]] of Animal.prototype

## Mixing-in classes

JavaScript provides no native mixing-in mechanism so to
achieve it you, either need to augment the prototype after the definition or effectively
inherit from your mixins (as if they are superclasses).

Augmenting a prototype with your mixins is the simplest approach. We can achieve this
by specifying mixins as objects and then adding them to prototype of a class via a
convenient method such as Object.assign:

```javascript
const fooMixin = { foo() {} };
const bazMixin = { baz() {} };
class MyClass {}
Object.assign(MyClass.prototype, fooMixin, bazMixin);
```

This approach, however, does not allow MyClass to override its own mixin methods
To achieve a more generalized mixin approach, we can use inheritance.This
can most easily be achieved by so-called Subclass Factories. These are essentially just
functions that themselves return a class that extends a specified super-class:

```javascript
const fooSubclassFactory = (SuperClass) => {
  return class extends SuperClass {
    fooMethod1() {}
    fooMethod2() {}
  };
};
```
