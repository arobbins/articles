# Is everything in JavaScript an Object?

I always found this statement confusing: "Everything in JavaScript is an Object". What did they mean by this? How can a Function or an Array be an Object? The awnser is deceptively simple.

However before we tackle this question, we need to understand how the different data types are cateogrized in JavaScript. There are two data types in JavaScript&mdash;Primitives and Objects. JavaScript, The Definitive Guide 6th Edition Davig Flanagan pg 29

| Primitive Types | Object Types |
|-----------------|--------------|
| Numbers         | Functions    |
| Strings         | Arrays       |
| Booleans        | Objects 		|
| Null        		|              |
| Undefined       |              |

Based on this categorizing, the simple anwser is no, not everything in JavaScript is an Object. Only types that belong to that category are Objects. But what differeniates Primitives from Objects? And more importantly, what do people <em>really mean</em> when they say "everything" or "almost everything" in JavaScript is an Object"?

From my experience, what people really mean when they talk about types being "object-like" is their mutablity&mdash;specically&mdash;the ability to add and remove properties to them. For example, because Functions and Arrays are objects at their core, you can add properties to them just like any object literal.

```js
var func = function() {};
func.firstName = "Andrew";
func.name;
--> "Andrew"

var arry = [];
arry.age = 26;
arry.age;
--> 26
```

However because Primitive types are immutable, as a consequence we're unable to assign properties to them. The parser will immediately discard them at read-time. http://www.2ality.com/2011/03/javascript-values-not-everything-is.html

```js
var me = "Andrew";
me.lastname = "Robbins";
me.lastname;
--> undefined

var num = 10;
num.prop = 11;
num.prop;
--> undefined
```