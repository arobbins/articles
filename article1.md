# Is everything in JavaScript an Object?

For some reason, I was always confused by this statement: "Everything in JavaScript is an Object". What did they mean by this? How can a Function or an Array be an Object? The awnser is deceptively simple.

Before we tackle the main question before us, we need to understand the different data types in JavaScript.

JavaScript is divided into two main types -- Primitives and Objects. The Primitive types are numbers, strings, booleans, null, and undefined. The Object types are Functions, Arrays, and Objects.

JavaScript, The Definitive Guide 6th Edition Davig Flanagan

So the quick anwser is no. Not everything in JavaScript is an Object. Only Functions, Arrays, and Objects are ... objects.

In the past, I was confusing myself by


Object everything
In JavaScript, almost everything is an object. All primitive types except null and undefined are treated as objects. They can be assigned properties (assigned properties of some types are not persistent), and they have all characteristics of objects.
https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Working_with_Objects


Primitive types are passed by value and are immutable
https://www.youtube.com/watch?v=mh-hPzDfb_Q

Reference types are passed by reference and are mmutable