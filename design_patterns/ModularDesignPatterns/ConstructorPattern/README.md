# Constructor Patterns

The Constructor pattern uses a singular constructor and then manually fills its prototype
with methods and properties.

Typically, it begins with the definition of a constructor as a function declaration:

```javascript
function Book(title) {
  // Initialization Logic
  this.title = title;
}
```

This would then be followed by assigning individual methods to the prototype:

```javascript
Book.prototype.getNumberOfPages = function() { /* ... */ };
Book.prototype.renderFrontCover: function() { /* ... */ };
Book.prototype.renderBackCover: function () { /* ... */ };
```

The instantiation of a constructor would be via the new keyword

```javascript
const myBook = new Book();
```

This creates a new object that has an internal [[Prototype]] of the constructor's
prototype (that is, our object, which contains getNumberOfPages, renderFrontCover,
and renderBackCover).

## When to use the Constructor pattern:

The Constructor pattern is useful in scenarios where you wish to have an abstraction that
encapsulates the concept of a noun, that is, a thing that would make sense to have an
instance of.

If you're not sure whether the Constructor pattern is applicable, consider whether the
following questions are true:

- Is the concept expressible as a noun?
- Does the concept require construction?
- Will the concept vary between instances?
