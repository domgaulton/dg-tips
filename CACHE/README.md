# Cache

## Use Local Storage for Cache (react.js)


```js
  constructor(props) {
    super(props);
    this.state = {
      array: [],
    };
  }

  componentDidMount() {
    if (this.checkLocalStorage()) {
      // Set state from local storage
      this.setState({
        array: this.checkLocalStorage(),
      });
    }

    // Also call API in background, retrieve data and set time key
    api().then(data => {
      data.forEach(item => {
        console.log(item);

        // if item does not exist in local storage
        const itemExists = this.state.array.some(
          x => x.id === item.id,
        );
        if (!itemExists) {

          // Add it to the state
          this.setState({
            array: [...this.state.array, item],
          });

          // Update local storage and set timestamp
          saveToLocalStorage('array', JSON.stringify(this.state.array),);
          saveToLocalStorage('arrayTS', Date.now());
        }
      });
    });
  }

  checkLocalStorage() {
    const timeArraySaved = retrieveFromLocalStorage('arrayTS');
    const localArraySaved = JSON.parse(retrieveFromLocalStorage('array'));
    const now = Date.now();
    const minutesLimit = 15;
    const cacheLimit = minutesLimit * 60 * 1000;
    const timeDifference = now - timeArraySaved;
    if (
      timeArraySaved &&
      localArraySaved &&
      localArraySaved.length &&
      (cacheLimit > timeDifference || !window.navigator.onLine) // if offline ignore cache limit
    ) {
      return localArraySaved;
    }
  }
```
