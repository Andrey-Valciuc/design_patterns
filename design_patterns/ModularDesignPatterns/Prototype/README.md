# The Prototype Pattern

The Prototype pattern involves using plain objects to act as templates for other objects.
The Prototype pattern extends this template object directly without fussing with instantiation
via new or Constructor.prototype objects.

Typically, first will be created an object to act as a template. In the case of an
inputComponent abstraction, it may look like this:

```javascript
const inputComponent = {
  name: "Input Component",
  render() {
    return document.createElement("input");
  },
};
```

Using our inputComponent template, we can then create (or instantiate) specific instances
using Object.create:

```javascript
const inputA = Object.create(inputComponent);
const inputB = Object.create(inputComponent);
```

This means that any properties accessed on the new object will be looked for on thePrototype if they are not available on
the object itself. As such, we can treat the resulting object just like any other classical instance:

```javascript
inputA.render();
```

This means that we can create individual instances with slightly less code:

```javascript
const inputA = inputComponent.extend();
const inputB = inputComponent.extend();
```

## When to use the Prototype pattern:

The Prototype pattern is most useful in scenarios where you have an abstraction that will
have varying characteristics between instances (or extensions) but does not require
construction.

Imagine a scenario in which we need to represent sandwich data. Every sandwich has a
name, a bread type, and three slots for ingredients. For example, here is the representation
of a BLT:

```javascript
const theBLT = {
  name: "The BLT",
  breadType: "Granary",
  slotA: "Bacon",
  slotB: "Lettuce",
  slotC: "Tomato",
};
```

We may wish to create an adaptation of the BLT, reusing most of its characteristics except
the Tomato ingredient, which will be replaced with Avocado. We could simply clone the
object wholesale, by using Object.assign to copy all the properties from theBLT to a
fresh object and then specifically copying over (that is, overwriting) slotC:

```javascript
const theBLA = Object.assign({}, theBLT, {
  slotC: "Avocado",
});
```

We could equally represent this data using straightforward classes but with such basic data
that may be overkill.
