# Firebase

## Installing
* `npm install -g firebase-tools` then head to directory and `firebase init`

## Useful CLI commands
* `firebase serve` - create a local server to test functions
* `firebase deploy` - deploy your changes

## Sample functions
* https://github.com/domgaulton/functions-samples/tree/master/github-to-slack

## Firebase Config File
Where you might have something like and import;

```
slack: {
  api: 'stringXYZ',
  user: 'dgtips'
},
something_else: {
  api: 'fbXYZ',
  user: 'domfire'
}
```

You can set config with firebase as follows
* `firebase functions:config:set slack.api="stringXYZ" something_else.api="fbXYZ"`