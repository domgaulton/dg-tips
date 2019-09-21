# React Tips

## Target specific nested state object and update

* Where `stateObject` is the wrapper state object
* Where `itemObject` is the object you want to update
* `uniqueId` is the unique reference to update
* `targetId` is the variable you are using as the key to finding and updating the specific `itemObject` in the `stateObject`

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

* Where `info` is array
* Primary user details are saved uniquly
* Dynamic state names for rest of the fields differently
* Notice that we slice the first user from the forEach loop

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

## React.Context
* Allows global data to be accessed and set!
1. Set up your context DataProvider.js
```
import React, { Component } from 'react';

// see React.creactContext() documentation;
const Context = React.createContext();

// create a DataProvider
class DataProvider extends Component {
  constructor(props) {
    super(props);
    this.state = {
      data: {},
      fact: false,
      loaded: false,
      setFunction: (data) => this.handleSetFunction(data),
    };
  }

  // Here we have a function that updates the state and global data
  handleSetFunction = data => {
    this.setState({
      data,
      loaded: true,
    })
  }

  // Return the state as the value of the context provider
  render(){
    return (
      <Context.Provider value={this.state}>
        {this.props.children}
      </Context.Provider>
    );
  }
}

// Export provider
export default DataProvider;

// Export named function that allows people to consume the data
export const DataConsumer = Context.Consumer;
```
2. `DataProvider` (default export) - Then in App route you wrap a provider around the component
```
import React from 'react';
import DataProvider from "./context/DataProvider";

function AppRouter() {
  return (
    <DataProvider>
      <App/>
    </DataProvider>
  );
}

export default AppRouter;

```
3. `DataConsumer` (named export) - And finally on each component pass the state data from above from the exported `DataConsumer` to the component to access state data.
```
import React, { Component } from 'react';
import { DataConsumer } from "./context/DataProvider";


class Something extends Component {
  render(){
    return (
      <div className="App">
        <h1>Create Tavern</h1>
         {this.props.newData}
      </div>
    );
  }
}

const SomethingUpdate = props => (
  <DataConsumer>
    {({ newData }) => (
      <Home
        // remember to spread the existing props otherwise you lose any new ones e.g. 'something' that don't come from the provider
        {...props}
        newData={newData}
      />
    )}
  </DataConsumer>
);

export default SomethingUpdate;
```

## useState
* No need for a component with React
```js
import React, { useState } from 'react';

function Application(props) {

  // think of this as `this.state.data` and `this.setState({data: bool )`
  const [data, set_data] = useState(false);

  const handleSetData = () => {
    set_data(true);
  }

  return data ? (
    <Something />
  ) : (
    <SomethingElse setData={handleSetData}/>
  );

}

export default Application;


