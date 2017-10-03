---
layout: post
title: Vanilla JS // Closures
comments: true
---

In the Vanilla JS series, we will go through the basic and not-so-basic concepts in plain old JavaScript, starting with Closures.


<img class="no-shadow" alt="D3.js logo" src="/Front/assets/img/5/vanilla.jpg" style="width: 40%; height: auto; display: block; margin: 0 auto;"/>
<p style="text-align: center; font-size:15px;"><em>Vanilla</em></p>

### **What is a Closure?**

According to [MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Closures), 

>A closure is the combination of a function and the lexical environment within which that function was declared.

The things here to note are **function** and **lexical** environment. Here is a nested JavaScript function.

```javascript
function factor(a) {
  var b = a;
  return function product(x) { // a closure; uses variable declared in the parent function
    return b * x;
  };
}

var twice = factor(2); // an instance of the factor function
console.log(twice(5)); // 10

var thrice = factor(3); // another instance of the factor function
console.log(thrice(5)); // 15

// and another instance of the factor function
console.log(twice(10) + thrice(10)) // 50

```
Note the following three points.

I. The function `factor` creates a **local** variable `b` that is used by the inner function `product`. 

II. Since `b` is outside of `product`, it forms the **lexical** environment of `product`.

III. `Twice` and `Thrice` are the two instances of the function `factor` *alive* simultaneously, each having a different value of `b`. 

This feature of JavaScript, where a specific instance of a local variable is used in an enclosing function is called a **Closure**. The function `product` is a Closure that *closes* over the instantaneous value of `b`. Closure allow us to use multiple instances of the local variable without worrying about their lifetime or interference.

In other words, when we declare a function within a function, the inner function is recreated whenever the outer function is called. Each instance of the inner function preserves its environment and can co-exist without any overlap. This is called a Closure.


