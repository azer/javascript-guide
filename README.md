* [Write Functions As Much As Possible]()
* [Compose Large Abstractions From Small Modules]()
* [Avoid `new`, `prototype` and `this`](#avoid-new-prototype-and-this)
* [Prefer Embedding Over Inheritance](#prefer-embedding-over-inheritance)

## Write Functions As Much As Possible.
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
