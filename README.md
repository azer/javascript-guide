* [Write Functions As Much As Possible](#write-functions-as-much-as-possible)
* [Compose Large Abstractions From Small Modules]()
* [CommonJS Everywhere](#commonjs-everywhere)
* [Require & Export on Top](#require-export-on-top)
* [Avoid `new`, `prototype` and `this`](#avoid-new-prototype-and-this)
* [Prefer Embedding Over Inheritance](#prefer-embedding-over-inheritance)

## Write Functions As Much As Possible.

And define them with `function` keyword:

```js
foo()
bar()

function foo(){}
function bar(){}
```

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
