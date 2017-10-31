---
layout: post
title: Vanilla JS // Slice vs Splice 
comments: true
---

In this post, we will discuss the most common rookie mistake in JavaScript &#8212; difference between slice() and splice().

<img class="no-shadow" alt="Vanilla" src="/Front/assets/img/5/vanilla.jpg" style="width: 40%; height: auto; display: block; margin: 0 auto;"/>
<p style="text-align: center; font-size:15px;"><em>Vanilla</em></p>


### **slice()**

>The slice() method returns a [shallow copy](https://stackoverflow.com/questions/184710/what-is-the-difference-between-a-deep-copy-and-a-shallow-copy) of a portion of an array into a new array object selected from begin to end (end not included). The original array will not be modified.

The slice() method takes two arguments (both optional).

* **Begin:** The starting index, zero by default.
* **End:** The last index that will not be included. If not defined, it takes the value of the length of the array.

slice() then creates a *new* array by *slicing* the original one from `Begin` to `End - 1`.

Let's see this in action.

```javascript
let a = [1, 2, 3, 4, 5];

let b = a.slice(); // select elements from 0 to a.length - 1
let c = a.slice(0, 2); // select elements from 0 to 2 - 1

console.log(a); // [1, 2, 3, 4, 5]
console.log(b); // [1, 2, 3, 4, 5]
console.log(c); // [1, 2]
```
The point here to note is that slice() **does not** change the original array.

### **splice()**

>The splice() method changes the contents of an array by removing existing elements and/or adding new elements.

splice() takes three (or more) arguments.

* **Begin:** The starting index, zero by default.
* **deleteCount:** The number indicating the elements to remove. If zero, then nothing will be removed. If undefined or greater than the length of the array, all the elements will be removed.
* **items:** The element(s) to be added to the array starting from `Begin` index.

Here are some examples.


```javascript
let a = ["a", "b", "c", "d", "e"];

let b = a.splice(0); // start at 0 and remove all elements

console.log(a); // []
console.log(b); // ["a", "b", "c", "d", "e"]
```

```javascript
let a = ["a", "b", "c", "d", "e"];

let b = a.splice(0, 2); // start at 0 and remove 2 elements

console.log(a); // ["c", "d", "e"]
console.log(b); // ["a", "b"]
```

```javascript
let a = ["a", "b", "c", "d", "e"];

let b = a.splice(0, 0, "x", "y"); // start at 0, remove 0 elements, insert "x" and "y" from index 0

console.log(a); // ["x", "y", "a", "b", "c", "d", "e"]
console.log(b); // []
```

The point here to note is that splice() **does** change the original array.

### **Noting the difference**

**splice()** mutates the array while **slice()** does not. You can easily remember this by noticing the "p" in splice as if the word slice got mutated and grew a **p**.

* **slice():** No mutation. Does not change the original array.
* **splice():** Growth of a **p**. Mutation. Changes the original array.

### **Furthermore**
MDN resources are the best. Ever. Damn.

* [Array.prototype.splice()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/splice)
* [Array.prototype.slice()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/slice)