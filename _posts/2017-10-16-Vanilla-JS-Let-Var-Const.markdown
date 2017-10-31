---
layout: post
title: Vanilla JS // Var vs Let vs Const 
comments: true
---

In this post, we will discuss the two new ways to declare a variable &mdash; Let and Const as introduced in ES6. 

<img class="no-shadow" alt="Vanilla" src="/Front/assets/img/5/vanilla.jpg" style="width: 40%; height: auto; display: block; margin: 0 auto;"/>
<p style="text-align: center; font-size:15px;"><em>Vanilla</em></p>

But first, what is ES6? In the most basic (and laziest) terms, it is the new JavaScript version as released by [ECMA](https://www.ecma-international.org/), the standards body for JavaScript. ES6 comes with some new and shiny features such as let and const. You may read the ES6 official docs [here](https://www.ecma-international.org/ecma-262/6.0/).

OK, let's move on.

### **What is wrong with using var?**

JavaScript is a forgiving language. Here is an example.

```javascript
var a = 10;
var a = 20;

console.log(a); // 20
```
Multiple declarations of the same variable, cool. Here is another.

```javascript
function foo() {
  for (var i = 0; i < 10; i++) {
  // do something
  }
  console.log(i); // 10
}
```
The fact that `console.log(i)` returns `10` is strange because we expect `i` to exist only its local scope i.e. inside the loop. In the previous version of JavaScript (or ES5), we had only one kind of scope and that was the **function scope**. 

Another thing to note is that in JavaScript, the variables are **hoisted**. In a functional scope, JS pushes the variable declarations to the top of the scope. In the previous example, if we remove `var i` declaration from the function, JS will first try to find the declaration in the functional scope and then go all the way up to the window scope.

This is a very dangerous way to declare a global variable!!! An easy way to avoid this is by placing `"use strict";` at the top. 

So we see that there are quite a many disadvantages of var. Enter **let**.

### **Let and Const**

Let is the newer, smarter var. 

```javascript
let a = 10;
let a = 20;

console.log(a); // Uncaught SyntaxError: Identifier 'a' has already been declared
```
Boom! No more accidentally declaring the same variable twice. Also, unlike var, let and const are **block scope**. They only exist within `{}`.

```javascript
{
  let a = 10;
}

console.log(a); // Uncaught ReferenceError: a is not defined
```
Sweeet, now JS feels like a normal language.

Now if you're dead sure that you will not need to change a variable's value ever again, use **const**.

```javascript
const a = 10;
a = 20;

console.log(a); // Uncaught SyntaxError: Assignment to constant variable.
```

However, const does not guarantee complete immutability. 

```javascript
const x = {
  a: 5,
};

x.a = 6;

console.log(x.a); // 6
```

But it does prevent a complete rewrite of the variable.

```javascript
const x = {
  b: 5,
};

console.log(x.b); // Uncaught SyntaxError: Identifier 'x' has already been declared.
```

So why use const instead of just let? To **minimize mutable state**. It allows the code to be a bit more manageable as there is one less moving part. Once we define `const x = 10;`, we are sure its value will never be changed by any other process.

### **Furthermore**

Hope you liked this post and start (or continue) to use let and const instead of var. Check out [MDN web docs](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/let) to know more about them!
