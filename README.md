* [Code Functions As Much As Possible](#code-functions-as-much-as-possible)
* [Compose Large Abstractions From Small Modules](#compose-large-abstractions-from-small-modules)
* [Write Declarative Code](#write-declarative-code)
* [NPM Everywhere](#npm-everywhere)
* [Require & Export on Top](#require--export-on-top)
* [Avoid `new`, `prototype` and `this`](#avoid-new-prototype-and-this)
* [While Loops are Simpler](#while-loops-are-faster-and-simpler)
* [Declare Variables Outside of Statements](#declare-variables-outside-of-statements)

## Code Functions As Much As Possible.

* Create functions that does only one thing.
* Avoid declaring functions with `var` statement

```js
foo()
bar()

function foo(){}
function bar(){}
```

## Compose Large Abstractions From Small Modules

* Create modules that does one thing. 
* Create repositories for modules and publish/open source them on NPM and Github if possible.
* Never couple your code with any dependency doing more than it should
* Avoid frameworks

A good read about this topic: http://substack.net/many_things

## Write Declarative Code

* Write less code
* Write code that tells what it does briefly
* Choose simple & short variable names

## NPM Is Everywhere

* Modularize your JS in CommonJS.
* Use [browserify](http://github.com/substack/node-browserify)
* Avoid other module systems like RequireJS.

## Require & Export on Top

```js
var foo = require('foo')
var bar = require('./bar')

module.exports = {
  qux: qux,
  corge: corge
}

function qux(){}
function corge(){}
```

## Avoid `new`, `prototype` and `this`

Functions returning objects are much simpler, more replaceable and reusable:

```js
var smith = Child('Joe', 'Smith')

function Child(parent, name){
  return {
    parent: parent,
    name: name
  }
}
```

And keep your code available for functional programming:

```js
var JoeChild = partial(Child, 'Joe')

var smith = JoeChild('Smith')
var kat = JoeChild('Kat')

smith.parent
// => Joe

kat.parent
// => Joe
```

## Declare Variables Outside of Statements

Declaring variables inside of a statement will make your code work and look less consistent. For example, below code will fail when you run it:

```js
foobar
```

With the error of "ReferenceError: foobar is not defined". But following code will not fail;

```js
foobar

if (false) {
  var foobar
}
```

For having better consistency, declare the variable on top of your statement;

```js

var foobar

if (false) {
  foobar = whatever
}
```

## While Loops Are Faster And Simpler

While loops are faster than for loops, and they're much simpler. Here is an example;

```js
var i = 10

while (i--) {
  console.log(i)
}
```

This will output from 9 to 0. If you'd like the other way:

```js
var i = -1

while (++i < 10) {
  console.log(i)
}
```

![](https://dl.dropboxusercontent.com/s/prfjx7c33zm8x9o/npmel_0.jpg)
