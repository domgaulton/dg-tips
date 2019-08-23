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

## setState from two different sources in one go (map through array)

- Where `info` is array
- Primary user details are saved uniquly
- Dynamic state names for rest of the fields differently
- Notice that we slice the first user from the forEach loop

```js
const new_existingState = {
  ...this.state.existingState,
  primary-name: info[0].name,
  primary-id: info[0].id
};

// Loop through 2nd user onwards
info.slice(1).forEach((elem, index) => {
  const dynamicName = `user-${index}-name`;
  const dynamicId = `user-${index}-id`;
  new_existingState[dynamicName] = elem.name;
  new_existingState[dynamicId] = elem.id;
});

// Set state of entire object above
this.setState(
  {
    bookingModel: newBookingModel
  }
);
```
