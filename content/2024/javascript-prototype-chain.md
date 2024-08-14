---
title: 'JavaScript Prototype Chain'
date: 2024-08-14T12:55:43+08:00
draft: false
categories:
tags: [javascript]
---

prototype chain is inheritance mechanism in JavaScript.

JavaScript objects have a link to prototype objects.

When trying to access a property of an object, the property will not only be sought on the object, but on the prototype of the object.

```javascript
const o = {
  a: 1,
  b: 2,
  // __proto__ sets the [[Prototype]]. It's specified here
  // as another object literal.
  __proto__: {
    b: 3,
    c: 4,
  },
};

// o.[[Prototype]] has properties b and c.
// o.[[Prototype]].[[Prototype]] is Object.prototype (we will explain
// what that means later).
// Finally, o.[[Prototype]].[[Prototype]].[[Prototype]] is null.
// This is the end of the prototype chain, as null,
// by definition, has no [[Prototype]].
// Thus, the full prototype chain looks like:
// { a: 1, b: 2 } ---> { b: 3, c: 4 } ---> Object.prototype ---> null
```

