# React Tips

## Target specific item in state and update

- Where `stateObject` is the object
- `uniqueId` is the unique reference to update
- `targetId` is the variable you are using as the key to finding the item in the `stateObject`

```js
this.setState(prevState => ({
  stateObject: prevState.groupBookingData.map((data, index) =>
    data.uniqueId === targetId
      ? {
          ...data,
          newData1: "This",
          newData2: "Is",
          newData3: "Smart"
        }
      : data
  )
}));
```
