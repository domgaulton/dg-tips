# Console

## Window Object

- `console.log(window)` or type in `window` into console to see methods functions etc that are accesible via the window object e.g. console > log!

## console.log()
- Thanks Wes Bos!
```js
const foo    = { name: 'tom',   age: 30, nervous: false };
const bar    = { name: 'dick',  age: 40, nervous: false };
const baz    = { name: 'harry', age: 50, nervous: true };
```

### Custom Styles
- Add %c to string then second param is css
- `console.log('%c My Friends', 'color: orange; font-weight: bold;' )`
- `console.log({ foo, bar, baz });`

### Console Table
- Console log comparable table
- `console.table([foo, bar, baz])`

### Console Timer
- Start and end timer after function completes
```js
console.time('abc')

let i = 0;
while (i < 1000000) { i ++ }

console.timeEnd('abc')
```

### Console Trace Logs
```js
const deleteMe = () => console.trace('bye bye database')
deleteMe()
```