# Call it Back

This Readme tries to better introduce the concept of callbacks to those new to it, I assume you have a basic understanding of JavaScript and know what functions are.

## Functions all the way

#### Functions can do it all 

- A function is a first-class object.
- has methods, check https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Function/prototype#Methods
- has properties, check https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Function/prototype#Properties 
- can be assigned to a variable, 
```js
function foo() {...}
var someFunction = foo;
```
or 
```js
var someFunction = function() {...};
```
Notice the second definition uses anonymous functions.
- And a lot more...

#### What else?

- what are these lines doing? can we assign a function to an object?

```js
var obj = {1: function(){ console.log("The first property");}, 2: "string"};
obj[1]();
```
Answer: Yes you can, if you run these lines you'll get "The first property" logged to your console.
Notice that we invoke the function by adding parenthesis to `obj[1]`, without them all we'll get is the function itself (lines of code, that mean nothing if not executed!).

- And arrays? can a function be a value in an array?
Yes! it can.
what is this code doing?
```js
var functionsArray = [function(){console.log("I'm the first value in the array");}, function(){console.log("I'm the second");}, function(){console.log("Hello I'm third");}];
functionsArray.forEach(function(fun){
	fun();
});
```
`fun()` will execute all the functions in the array.


## So, what's a callback then?

A callback function, also known as a higher-order function, is a function that is passed to another function.
We already know that a function can do anything any object can do, that also means they can be passed around as arguments, for example:
```js
function foo (myCallBack){
 	myCallBack();
}
```
foo expects one argument as an input, this argument needs to be a function, since we call it.
trying to execute this line 
```js
foo("a string");
``` 
would error with the following: `TypeError: myCallBack is not a function`, this is happening because we use the argument myCallback as a function.

_How do I send a function though_ :thinking:?

As mentioned before, functions are objects in every way, so a function definition can be passed as an argument too:
```js
function theCallBack(){
	console.log("Jack, come back");
}
foo(theCallBack);
```
Here we can see `theCallBack` passed to foo as an argument and as expected this will log `Jack, come back`.

Another way you can pass a function is by using anonymous functions (a function doesn't have to have a name, same if we pass `3` instead of `x` with a value of 3), this is how it would look like:
```js
foo(function(){
 	console.log("expected a function, got an anonymous one :|");
});
```
