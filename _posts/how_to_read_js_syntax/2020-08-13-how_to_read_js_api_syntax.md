---
title: How to read the syntax section in the Javascript docs
date: 2020-08-13 11:00:47 -07:00
tags: [blog, javascript, syntax, API]
description: All the services are free, a source code this site placed on github repository and intergration with netlify service, another service that you can use is github page for hosting your own static site.
---

## I've always wondered how to read the syntax portions of APIs
Admittedly I used to skip this portion of the API, opting to go straight for the code examples. Thought I'd learn how to read it properly now.

[From MDN, syntax for Array.prototype.forEach()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/forEach)
> ***arr***.forEach***(callback(currentValue [, index [, array]])[, thisArg])***

1. The unitalicized forEach is a literal. Everything else means we're substituing with our own values.
1. [] means the argument is optional

So in this example, all we need is an array and a callback function with a currentValue parameter to use forEach().


### TL;DR for how to read API syntax
- Underlined words or unitalicized words are considered literals, and are typed just as they appear.
- Square brackets ( **[ ]** ) around an argument indicate that the argument is optional.
- Ellipses ( **...** ) are used to show that the previous argument-prototype may be repeated.
- An argument beginning with a minus sign ( **-** ) is often taken to mean some sort of flag argument even if it appears in a position where a file name could appear.


### References
[Link to StackOverflow](https://stackoverflow.com/questions/10925478/how-to-interpret-api-documentation-function-parameters)