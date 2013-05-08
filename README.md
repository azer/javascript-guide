* [Code Functions As Much As Possible](#code-functions-as-much-as-possible)
* [Compose Large Abstractions From Small Modules](#compose-large-abstractions-from-small-modules)
* [Write Declarative Code](#write-declarative-code)
* [CommonJS Everywhere](#commonjs-everywhere)
* [Require & Export on Top](#require--export-on-top)
* [Avoid `new`, `prototype` and `this`](#avoid-new-prototype-and-this)
* [Prefer Embedding Over Inheritance](#prefer-embedding-over-inheritance)
* [Write Code Examples in Simplified Syntax](#write-code-examples-in-simplified-syntax)

## Code Functions As Much As Possible.

And define them with `function` keyword, not `var`:

```js
foo()
bar()

function foo(){}
function bar(){}
```

## Write Declarative Code

More info: https://github.com/azer/declarative-js

## CommonJS Everywhere

Modularize your both backend and frontend code in CommonJS. Avoid other module systems like RequireJS.

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

## Compose Large Abstractions From Small Modules
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
