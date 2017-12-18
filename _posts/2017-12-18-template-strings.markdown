---
layout: post
title: Template Literals in Javascript
date: 2017-12-18
---

<p class='intro'><span class='dropcap'>T</span>here are two ways to write strings in javascript - single quotes and double quotes. With ES6, we have another way to write strings using backticks (``). This is called Template literal. Let's dive into details!
</p>

### String Interpolation

Before ES6, if wanted to put a variable in the string we had to concatenate it. Every other language provided some sort of placeholder for variables in the string but not javascript. Thankfully with Template literal, we can put variables inside `${var}` and its value will be reflected in the string.

```js
const name = "Elliot";
const age = 30;

let sentence = `My name is ${name} and I am ${age} years old.`;

console.log(sentence); // My name is Elliot and I am 30 years old.
```

Pretty cool right? It gets even cooler when you know that you can put any javascript expression between `${expression}`. The expressions will be evaluated and their values will be reflected in strings. Let's see an example:

```js
const a = 10;
const b = 20;

let sentence = `The sum of ${a} and ${b} is ${a + b}.`;

console.log(sentence); // The sum of 10 and 20 is 30.
```

### Multiline Strings

With backticks we can also write multiline strings as below:

```js
const sentence = `This is on first line.
This is one second line.`;

console.log(sentence);
// This is on first line.
// This is one second line.
```

### Tagged Template Literals

Whenever we use backticks to generate a string, a function gets called. By default, this function concatenates the values and string. However, we can do any modification to values if we want to do inside the function. We need to put a function name before starting backtick. This function will get called with strings and values. Let's see an example:

```js
const person = "Elliot";
const age = 28;

let str = myTag`that ${person} is a ${age}`;

console.log(str); // that Elliot is a youngster

function myTag(strings, ...values) {
  console.log(strings); // ['that ', ' is a', '' ]
  console.log(values); // ['Elliot', 28]

  let str0 = strings[0];
  let str1 = strings[1];

  let person = values[0];
  let age = values[1];

  let ageStr = "";
  if (age > 99) {
    ageStr = "centenarian";
  } else {
    ageStr = "youngster";
  }

  return str0 + person + str1 + ageStr;
}
```

This is all for this post. Thanks for reading!
