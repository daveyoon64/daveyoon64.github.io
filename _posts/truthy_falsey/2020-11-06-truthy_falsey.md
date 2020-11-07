---
title: The truth about truthy falsey
date: 2020-11-05 11:00:47 -07:00
tags: [blog, javascript, truthy, falsey]
description: All the services are free, a source code this site placed on github repository and intergration with netlify service, another service that you can use is github page for hosting your own static site.
---

## I've learned a lot from reading open source projects!
Sometimes, I run into dense lines with a lot of information packed inside...

```javascript
function isString(obj) {
  return !!(obj === '' || (obj && obj.charCodeAt && obj.substr));
}
```
The function name gives us a hint that that function checks if an object is a string or not. But what the heck does the rest of it mean?

## Checking for blank strings
```javascript
obj === ''
```
We have to check is obj is a blank string. Why? `''` is a blank string and a falsey value in JavaScript. 

```javascript
// quick check that '' is falsey
if ('') {
  console.log('true');
} else {
  console.log('false');
}
// writes `false`
```
Since `''` is a string, we want to return `true`.

## Chaining || aka or
In JavaScript, the `or` operator evaluates the left and right side's truthy and falsey values in the following order:
1. If the left side is truthy, return that value.
2. If the left side is falsey, return the value on the right side.

In other words, as it evaluates left to right, it's trying to find `true` or truthy as soon as possible.

## obj?
This checks to see if `obj` exists and is truthy.

## obj.charCodeAt?
`charCodeAt()` takes an integer index and returns a UTF-16 value representing the character. 
```javascript
var obj = 'dave';
obj.charCodeAt(); 
// returns 100
```
If there's no argument, then it defaults to 0. 
So if `obj` is a string, the 0th character should be truthy.

## obj.substr?
`substr()` normally returns a substring, but in this case since there are no arguments, it'll return truthy if `obj` is a string or `undefined` otherwise, another falsey value.
```javascript
var obj = 'dave'
if (obj.substr) {
  console.log('true');
}
// write 'true' to console
```
## Chaining && aka and
In JavaScript, the `and` operator evaluates the left and right side's truthy and falsey values in the following order:
1. If the left side is falsey, return that value.
2. If the left side is truthy, return the value on the right side.

In other words, as it evaluates left to right, it's trying to find `false` or falsey as soon as possible. 

## So the right side is saying what?
So if it exists, the first character has a UTF-16 code, and `substr()` returns true, it's a string!

## And finally, the !!
`!!` converts a truthy or falsey value to its boolean value. Truthy becomes true and falsey becomes false.

### References
[MDN String.prototype.substr](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/substr)
[MDN String.prototype.charCodeAt](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/charCodeAt)
