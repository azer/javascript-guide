This repository records how I code JavaScript.

* [Code Functions As Much As Possible](#code-functions-as-much-as-possible)
* [Compose Large Abstractions From Small Modules](#compose-large-abstractions-from-small-modules)
* [Write Declarative Code](#write-declarative-code)
* [CommonJS Everywhere](#commonjs-everywhere)
* [Require & Export on Top](#require--export-on-top)
* [Modularize Required Data](#modularize-required-data)
* [Avoid `new`, `prototype` and `this`](#avoid-new-prototype-and-this)
* [Prefer Embedding Over Inheritance](#prefer-embedding-over-inheritance)
* [Write Code Examples in Simplified Syntax](#write-code-examples-in-simplified-syntax)

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

Write code that looks clean and describes what it wants to do. 

More info: https://github.com/azer/declarative-js

## CommonJS Everywhere

* Modularize your both backend and frontend code in CommonJS.
* Use [OneJS](http://github.com/azer/onejs) or [Browserify](http://github.com/substack/node-browserify). 
* Avoid other module systems like RequireJS.

## Require & Export on Top

```js
foo = require('foo')
bar = require('./bar')

module.exports = {
  qux: qux,
  corge: corge
}

function qux(){}
function corge(){}
```

## Modularize Required Data

Create modules for the data your program depends on. 
Example: https://github.com/azer/indev/blob/master/lib/look-up.js

## Avoid `new`, `prototype` and `this`

Functions returning objects are much simpler, more replaceable and reusable:

```js
smith = Child('Joe', 'Smith')

function Child(parent, name){
  return {
    parent: parent,
    name: name
  }
}
```

And keep your code available for functional programming:

```js
JoeChild = partial(Child, 'Joe')

smith = JoeChild('Smith')
kat = JoeChild('Kat')

smith.parent
// => Joe

kat.parent
// => Joe
```

## Prefer Embedding Over Inheritance

```js
qux = Qux()
qux.foo
// => true
qux.bar
// => true
qux.qux
// => true

function Foo(){
  return {
    foo: true
  }  
}

function Bar(){
  return {
    bar: true
  }
}

function Qux(){
  return {
    qux: true,
    foo: Foo(),
    bar: Bar()
  }
}

```

## Write Code Examples in Simplified Syntax

* Assume that all variables are already declared.
* Avoid semicolons

```js
foo = 123
bar = 456

function qux(){
  return foo + bar
}
```

![](https://dl.dropboxusercontent.com/s/prfjx7c33zm8x9o/npmel_0.jpg)
