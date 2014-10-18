# Is everything in JavaScript an Object?

I always found this statement confusing: "Everything in JavaScript is an Object". What did they mean by this? How can a Function or an Array be an Object? The awnser is deceptively simple.

However before we tackle this question, we need to understand how the different Data Types are cateogrized. In JavaScript, there are two Data Types: Primitives and Objects. (Object Types are also sometimes referred to as Reference Types).

http://www.ecma-international.org/publications/files/ECMA-ST/Ecma-262.pdf pg 2
JavaScript, The Definitive Guide 6th Edition Davig Flanagan pg 29
http://www.codecademy.com/courses/primitives-development-course/6/1
https://developer.mozilla.org/en-US/docs/Web/JavaScript/Data_structures#Data_Types

|: Primitive Types |: Object Types |
|-----------------|--------------|
| Numbers         | Functions    |
| Strings         | Arrays       |
| Booleans        | Objects 		|
| Null        		|              |
| Undefined       |              |
| Symbol (ES6)    | 					|

Based on this categorizing, the simple anwser is no, not everything in JavaScript is an Object. Only values that belong to that Type are Objects. Another way of looking at it, is any value that isn't a Primitive Type is an Object Type. But what differeniates Primitives from Objects? And more importantly, what do people <em>really mean</em> when they say "everything" or "almost everything" in JavaScript is an Object"?

## Mutability

From my experience, what people <em>really mean</em> when they talk about values being "object like" is their mutablity. More specifically, they're talking about the ability to add and remove properties. For example, because Functions and Arrays belong to the Object Type, you can add properties to them just like you would an object literal.

```js

var func = function() {};
func.firstName = "Andrew";
func.name; // "Andrew"

var arry = [];
arry.age = 26;
arry.age; // 26

```

However because Primitive Types are immutable, we're unable to assign properties to them. The parser will immediately discard them when attemping to read their value. http://www.2ality.com/2011/03/javascript-values-not-everything-is.html

```js

var me = "Andrew";
me.lastname = "Robbins";
me.lastname; // undefined

var num = 10;
num.prop = 11;
num.prop; // undefined

```

I also think it's useful to look at this from a more fundamental level. With regards to primitives, what does it really mean to say that their values cannot be changed? Consider the following code:

```js

1 = 2; // ReferenceError

```

This might seem like a silly example, but I think it shines a much needed light on exactly what we're talking about when we talk about mutability. When you type the number 1 in a JavaScript console, the compiler assigns that piece of data to the Primitive data type. Therefore when you attempt to change the number 1 to the number 2, it fails and probably has a heartattack under the hood.

## Comparison

Besides mutability, another important distinction between Primitive Types and Object Types is the way they're compared. Primitive Types are compared by value, while Object Types are compared by reference. What does this mean? Let's look at Primitives first. Consider the following code:

```js

"a" === "a"; // true

```
This is true because the value "a" is equal to "a". Simple. However what happens when we introduce variables into the picture? Nothing has changed except that we're now storing our Primitive Types into variables.

```js

var a = "a",
    b = "a";

a === b; // true

```

Since Primitive Types are compared by value, the result will true. The value of the variable a is exactly equal to the value of the variable b. In other words, "a" equals "a". Aristotle would be proud. However look at this. If we apply the same example to an Object Type, we get the opposite result.

```js

var a = {name: "andrew"},
    b = {name: "andrew"};

a === b; // false

```

Why is this? Object Types must reference the same object in order for its comparison to be true. As David Falagan puts it: <blockquote>"...we say that objects are compared by reference: two object values are the same if and only if they refer to the same underlying object."</blockquote>

Another example:

```js

var a = {name: "andrew"},
    b = a;

b.name = "robbins";

a === b; // true

```

This might seem strange at first, but look closer at what's happening. Because objects are part of the Object type, it's values are compared by reference. Reference to what? Reference to the same underlying object. In the above example, we're setting b equal to a. We didn't copy the object. We're simply creating a reference to the same object. Another way of looking at it is that we're pointing the variable b to a. Therefore when we mutate the "name" property on b, we're at the same time mutating the "name" property on a.

Back to Primitives, how would the same example apply to them?

```js

var a = "Andrew",
    b = a;

b = "Robbins";

a === b; // false

```

Remembering that Primitives are passed by value, when we set b equal to a, we're actually creating a new copy of a. Therefore when we change the value of b and then compare it to a, the value is not the same.

## Summary

JavaScript can be categorized into two Types: Primitives and Objects. The Primitive Types are Strings, Numbers, Booleans, undefined, null, and Symbol. The object Types are Functions, Objects and Arrays.

The two distinctions between Primitives and Objects are Mutability and Comparison.

Primitives are immutable. Another way of saying this is that their values can't be changed. On the other hand, Objects are mutable. Their values can be updated and changed.

Primitives are compared by value. When assigning one primitive to another, a copy is made. Objects on the other hand are compared by reference. Reference to what? Reference to the underlying object. When assigning one object to another, a reference is created. At this point, mutating a value on one object will update the value on the other object.

In the next section, we'll go over how these Types fit into the bigger picture by analyzing ProtoTypes, Constructors, and Inheritance.