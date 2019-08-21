# React Tips

## Target specific nested state object and update

- Where `stateObject` is the wrapper state object
- Where `itemObject` is the object you want to update
- `uniqueId` is the unique reference to update
- `targetId` is the variable you are using as the key to finding and updating the specific `itemObject` in the `stateObject`

```js
this.setState(prevState => ({
  stateObject: prevState.groupBookingData.map(itemObject =>
    itemObject.uniqueId === targetId
      ? {
          ...itemObject,
          newData1: "This",
          newData2: "Is",
          newData3: "Smart"
        }
      : itemObject
  )
}));
```
