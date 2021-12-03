# GraphQL

## Resources

- https://api.spacex.land/graphql/

## Queries

```js
{
  query (variables, limits, specificity etc) { // what are we looking for
    id // what do we want back?
  }
}
```

### Space X Example

#### Get rockets

- Query rockets, limited to 2

```js
{
  rockets(limit: 2) {
    id
  }
}
```

returns

```json
{
  "data": {
    "rockets": [
      {
        "id": "falcon1"
      },
      {
        "id": "falcon9"
      }
    ]
  }
}
```

#### Get specific rocket info

- Query specific rocket with id

```js
{
  rocket(id: "falcon1") {
    height {
      feet
      meters
    }
  }
}
```

returns

```json
{
  "data": {
    "rocket": {
      "height": {
        "feet": 73,
        "meters": 22.25
      }
    }
  }
}
```

## Variables and Directives

```js
{
  query lunch($size: String, $glutenFree: Boolean) { // set variables in search
    sandwich(size: $size) {
      bread @include(if: $glutenFree) { // only query this if search bool is true or use @skip

      }
    }
  }
}
```
