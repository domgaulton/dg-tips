# Javascript

## Get Elements
* `document.querySelector('# or .')` - The Document method querySelector() returns the first Element
* `document.querySelectorAll('# or .')` - returns a static (not live - doesn't update) NodeList

## Element Attributes
`element.attributes` - List of all element details! Very useful

## Terminology

### Functions
* Function or method

### Objects
* {items in curly brackets} - non-iterable

### Arrays
* [items in square brackets] - iterable

## Javascript ES6

### Arrow Functions
* from
```js
function someName(name){
  console.log(name)
}
```
* to
```js
const someName = (name) => {
  console.log(name)
}
```

### Const and Let (block scoping)
* `const x =` used when we don't want variable to change (note it can still be added to e.g. in an Array method such as `.push()`)
* `let y =` used when variable might change in new block of code / class / function. Inner Block Scope prevents variable being changed outside of variable and vica versa

### Template Literals (backticks)
* Great for injecting inline

```js
const name = 'Foo';
const hello = `Hello ${name}`
console.log(hello); // 'Hello Foo'
```

* Returning a string by sending literal as the string
```js
const age = (str, age) => {
  const ageStr = age > 5 ? `old` : `young`
  return `${str[0]}${ageStr} at ${age} years`
}

const calcAge = age`This thing is ${3}`
// This thing is young at 3 years
````

### Spread Operator (...)
* No need to concat anymore...

```js
let a = [7, 8, 9];
let b = [6, a..., 10];
console.log(b); // [6, 7, 8, 9, 10]
```

* Or we can add to an array from comma seperated list...

```js
function spread(...a) {
  console.log(a)
};
spread(1, 2, 3, 4, 5); // [1, 2, 3, 4, 5]
```

* or...

```js
function spreadAdd(...b) {
  let a = [1, 2, 3,...b];
  return a;
}

spreadAdd(4, 5, 6); // [1, 2, 3, 4, 5, 6]
```

### Destructuring
* Used instead of [0], [1] etc
```js
let items = [1, 2, 3, 4, 5]
let [a, b] = items;
console.log(b); // 2
```

* Destructure Object (old and new below)

```js
let wizard = {magical: true, power: 10}
// let magical = wizard.magical;
// let power = wizard.power;
let { magical, power } = wizard;
console.log(magical, power) // true 10
```

### Async Await

* Add async to the promise function

```js
const random = () => {
  return Promise.resolve(Math.random())
}

const sumRandomAsyncNums = async() => {
  const first = await random();
  const second = await random();
  const third = await random();

  // This won't run until each of the await functions are completed above
  console.log(`Result ${first + second + third}`);
}
```