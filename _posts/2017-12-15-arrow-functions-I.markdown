---
layout: post
title: Arrow functions in Javascript Part I
date: 2017-12-15
---

<p class='intro'><span class='dropcap'>T</span>oday, I am going to talk about Arrow functions. This is a hot topic in ES6. I have divided this post into two parts so that one post doesn't get awfully long. Let's get started!
</p>

### Arrow functions are short and nice

One of the main things about arrow functions is that they look nice and are shorter to write. Let's take a code example and compare normal functions with arrow functions.

```js
const numbers = [4, -3, 11, 44, -67, -34, 100, -201];

// I want a new array where all the numbers are postive

// Old way of doing this
const positiveNumbers = numbers.map(function(num) {
  return Math.abs(num);
});

console.log(positiveNumbers); // [4, 3, 11, 44, 67, 34, 100, 201]
```

We used a normal function inside `map`. We could write it in a more concise way using arrow functions. The first thing we need to do is get rid of keyword `function` and put a fat arrow (`=>`) after parameters.

```js
// This is how you do with arrow functions
const positiveNumbers = numbers.map((num) => {
  return Math.abs(num);
});
```

Okay, but it's still not that big of a deal. I don't understand the hype around them. That's because I haven't told you the full story yet. If you have only one parameter/argument then you can remove the parenthesis as well.

```js
const positiveNumbers = numbers.map(num => {
  return Math.abs(num);
});
```

### Implicit Return

Explicit return is when we write the keyword `return` in a function. In many callbacks like above, we only write one line of code and return it. In that case, we can remove the keyword `return` and also remove the curly braces.

```js
const positiveNumbers = numbers.map(num => Math.abs(num));
```

Aha! Now, it looks super cool. But remember you can do this only with one-liner functions. If a function takes no argument then you have to use empty parenthesis.

```js
const ones = numbers.map(() => 1);
console.log(ones); // [1, 1, 1, 1, 1, 1, 1, 1]
```

### Implicit return for an object

What if we need to return an object as implicit return. Suppose, we have an array of names and we want to return an array of objects, where each object has a name property.

```js
const names = ["Elliot", "Leon", "Vera"];

// This will not work because open curly braces for object
// will be confused with function's opening curly braces
const objNames = names.map(name => {
  name: name;
});

// Here's the correct way to do it
const objNames = names.map(name => ({ name: name }));
```
### Arrow functions are anonymous

All arrow functions are anonymous, meaning they don't have a name. However, we can put an arrow function inside a variable.

```js
const sayHi = name => {
  console.log("Hi! " + name);
};
```

This is it for this post. I will be talking about how arrow functions do not change the value of `this` in my next post. Thanks for reading.


**Recommended Course =>** <a href="https://es6.io" target="_blank" >ES6 For Everyone </a> by Wes Bos.
