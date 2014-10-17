# Is everything in JavaScript an Object?

For some reason, I was always confused by this statement: "Everything in JavaScript is an Object". What did they mean by this? How can a Function or an Array be an Object? The awnser is deceptively simple.

However before we tackle the this question, we need to understand how the different data types are cateogrized in JavaScript.

JavaScript is divided into two data types&mdash;Primitives and Objects.
| Primitive Types | Object Types |
|-----------------|--------------|
| Numbers         | Functions    |
| Strings         | Arrays       |
| Booleans        | Objects 		|
| Null        		|              |
| Undefined       |              |

The Primitive types are numbers, strings, booleans, null, and undefined. The Object types are Functions, Arrays, and Objects. Another way of looking at it is anything that is not a Primitive type is an Object.

JavaScript, The Definitive Guide 6th Edition Davig Flanagan pg 29

So the simple anwser is no, not everything in JavaScript is an Object. Only types that belong to that category.

With that said, the consequences of this paradigm are interesting to say the least&mdash;and as it was in my case&mdash;terribly confusing. First, because Functions and Arrays are objects, you can add properties to them just like any other object.

```js
var func = function() {};
func.firstName = "Andrew";
func.name;
--> "Andrew"
```
And in the case of Arrays...

```js
var arry = [];
arry.age = 26;
arry.age;
--> 26
```

However because Primitive types are immutable (can't be changed), we're unable to assign properties to them as a consequence. The parser immediately discards them. http://www.2ality.com/2011/03/javascript-values-not-everything-is.html

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

So what's going on behind the scenes?

## Prototypes

Every JavaScript object (non-primintive data types) has a prototype.