---
layout: post
title: Arrow functions in Javascript Part II
date: 2017-12-16
---

<p class='intro'><span class='dropcap'>H</span>ello, Everyone! In my last post, I wrote about how to write Arrow functions. Today, I am going to talk about how arrow functions do not change the value of <code>this</code>.
</p>

Let's start with an example and see, what I am talking about. I want to change the `background-color` of a button 500ms after it's clicked. Sounds simple right? Set a `click` listener on the button and inside it call a `setTimeout` function to change the color.

```html
<!DOCTYPE html>
<html>
<head>
 <title>Arrow Functions</title>
  <!-- CSS -->
  <style type="text/css">
  /* Changes background to red */
  .red {
    background: red;
  }
  </style>

</head>
<body>
  <button>Click Me!</button>

   <!-- Javascript -->
  <script type="text/javascript">

    const btn = document.querySelector('button');
    btn.addEventListener('click', function() {
      console.log(this); // button
      setTimeout(function() {
        console.log(this); // window!!
        this.classList.toggle('red');
      }, 500)
    });

  </script>
</body>
</html>
```

If you are like me and did what I did above then you must have got an error inside `setTimeout` function saying `cannot read property toggle of undefined`. That's because inside `setTimeout` function the value of `this` is `window` object rather than the `button`. This is not what we wanted. We didn't want to change the value of `this`. In such situations, we can use arrow functions. Arrow functions inherit the value of `this` from its parent scope. In this case, it's value will be `button` object. So, we can fix the code as below:

```js
const btn = document.querySelector("button");
btn.addEventListener("click", function() {
  console.log(this); // button
  setTimeout(() => {
    console.log(this); // window!!
    this.classList.toggle("red");
  }, 500);
});
```

### Default Arguments

In ES6, we can have default arguments in functions. This is not limited to just arrow functions but normal functions as well. Let's see an example.

```js
function sayHi(name = "Anku") {
  console.log("Hi! " + name);
}

sayHi(); // Hi! Anku

sayHi("Elliot"); // Hi! Elliot
```

In `sayHi` function, `name` parameter's default value is `Anku`. When we call `sayHi` without passing the argument, it uses the default value. But when we do pass the argument, it uses that instead. This feature allows us to set a default value for arguments.

This is all for this post. Thanks for reading. I am taking <a href="https://es6.io" target="_blank" >ES6 For Everyone </a> course by Wes Bos. This is a great course if you want to learn ES6. I highly recommend it.
