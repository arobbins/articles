# Is everything in JavaScript an Object?

For some reason, I was always confused by this statement: "Everything in JavaScript is an Object". What did they mean by this? How can a Function or an Array be an Object? The awnser is deceptively simple.

However before we tackle the this question, we need to understand how the different data types are cateogrized in JavaScript.

JavaScript is divided into two data types&mdash;Primitives and Objects. The Primitive types are numbers, strings, booleans, null, and undefined. The Object types are Functions, Arrays, and Objects. Another way of looking at it is anything that is not a Primitive type is an Object.

JavaScript, The Definitive Guide 6th Edition Davig Flanagan pg 29

So the simple anwser is no, not everything in JavaScript is an Object. Only types that belong to that category.


With that said, the consequences of this paradigm are interesting to say the least&mdash;and as it was in my case&mdash;terribly confusing. First, because Functions and Arrays are objects, you can add properties to those types like any object. For example:

```js
var func = function() {};
func.firstName = "Andrew";
func.name;
--> "Andrew"
```


Object everything
In JavaScript, almost everything is an object. All primitive types except null and undefined are treated as objects. They can be assigned properties (assigned properties of some types are not persistent), and they have all characteristics of objects.
https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Working_with_Objects


Primitive types are passed by value and are immutable
https://www.youtube.com/watch?v=mh-hPzDfb_Q

Reference types are passed by reference and are mmutable