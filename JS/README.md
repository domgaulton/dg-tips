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

## ES Lint
* Check if it's already installed `eslint -v`
* If not install using `npm install -g eslint`
* Note: You might need to install `npm install -g eslint-plugin-html` and `npm install -g eslint-plugin-markdown` the first time
* Run `eslint {filename.js}` in your terminal to see if it's working
* Create a eslintrc file - `touch .eslintrc` to create a configure file. 
* Add the below json object to the file WHERE;
* `env` : your environments that you'll be working with https://eslint.org/docs/user-guide/configuring#specifying-environments
* `extends` : what your checking your code against - To install airbnb follow https://github.com/airbnb/javascript/tree/master/packages/eslint-config-airbnb (npm5+ and global install `npx install-peerdeps --dev eslint-config-airbnb -g`)
* `rules` : overwrites the extends rules

```js
{
  "env": {
    "es6": true,
    "browser": true
  },
  // "extends": "eslint:recommended", // Use this before installing airbnb plugin
  "extends": "airbnb", // https://github.com/airbnb/javascript
  "rules": {
    "no-console": 0, // no-console: 0 (off) ... therefore console functions are allowed. Other rules 1) warn 2) error - https://eslint.org/docs/rules/no-console
    "no-unused-vars": 1 // warning rather than error for unused vars - https://eslint.org/docs/rules/no-unused-vars
  },
  "plugins": ["html", "markdown"] // used for JavaScript in HTML <script> or ```js Markdown
}
```

* Install `sublimelinter eslint` in package control
* Sublime and other text editors need the `.eslintrc` file in project or anywhere in root of app to query against.
