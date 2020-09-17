---
title: The new operator in JavaScript
date: 2020-09-16 16:16:47 -07:00
tags: [blog, javascript, new, operator]
description: All the services are free, a source code this site placed on github repository and intergration with netlify service, another service that you can use is github page for hosting your own static site.
---
## Why do you need to use the operator when creating an object?
I had always taken for granted the operator `new` in various languages. So I decided to dig a little deeper to see what it actually does in JavaScript.
Take for example, this JavaScript object, `Person`.
```javascript
function Person(name, superlative) {
  this.name = name;
  this.superlative = superlative;
}
```

So, what happens if I don't use `new`?
```javascript
var user = Person('Dave', 'awesome'); // what is user?
```
`user` in this case will be `undefined`. Why?

Running the good ol' Chrome debugger quickly tells us what's up.
![There's no `this` binding, so the implicit context will be window!](/assets/img/windowperson.jpg)

Since we didn't bind `this`, the JavaScript runtime will bind it to `window`, the default context.
In other words, you'll simply add the `name` and `superlative` properties to the `window` object.

## Let's try the `new` operator...
```javascript
var newuser = new Person('Dave', 'awesome');
// newuser now returns...
// Person {name: "dave", superlative: "kinda awesome"}
```
It properly returns an object! But how? The `new` operator does this for us **under-the-hood**.
```javascript
function Person(name, superlative) {
  // this = {}; <------ new operator
  this.name = name;
  this.superlative = superlative;
  // return this; <---- new operator
}
```
So now you'll get the JavaScript object with the `properties` you expect. By using 
`new`, the function `Person` now acts as a `constructor`.

### References
[Link to MDN documents](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/new)
