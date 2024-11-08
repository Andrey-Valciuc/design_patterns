# The Class Pattern

The Class pattern involves the creation of classes, analogous to classical OOP languages.
However, behind the scenes it uses the same prototypal mechanism that the Constructor pattern uses.

Here is an example of a basic class that abstracts the concept of a name:

```javascript
class Name {
  constructor(forename, surname) {
    this.forename = forename;
    this.surname = surname;
  }
  sayHello() {
    return `My name is ${this.forename} ${this.surname}`;
  }
}
```

The creation of a class via this syntax is effectively the creation of a constructor with an
attached prototype, hence the following code is exactly equivalent:

```javascript
function Name(forename, surname) {
  this.forename = forename;
  this.surname = surname;
}
Name.prototype.sayHello = function () {
  return `My name is ${this.forename} ${this.surname}`;
};
```

## When to use the Class pattern:

The Class pattern is useful when you have a self-contained concept that fulfills the following criteria:

- The concept is expressible as a noun
- The concept requires construction
- The concept will vary between instances of itself

Here are some [details](https://github.com/Andrey-Valciuc/design_patterns/tree/main/design_patterns/ModularDesignPatterns/ClassPattern/ClassPatternParticularities)
