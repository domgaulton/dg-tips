# Firebase

## Installing
* `npm install -g firebase-tools` then head to directory (or make new folder) and `firebase init`. You might need to make sure you're logged in `firebase login`
* In the firebase console make sure you have a Pay As You Go account so you can make external API calls

## Useful CLI commands
* `firebase serve` - create a local server to test functions
* `firebase deploy` - deploy your changes
* `firebase functions:config:get` see below

## Multiple hosting on one project
* Init project as normal with project id that holds your app - Add hosting to firebase.json
```
{
  "hosting": {
    "site": "XXXXX",
    "public": "build",
    "ignore": [
      "firebase.json",
      "**/.*",
      "**/node_modules/**"
    ]
  }
}

```
* Set up build command in your package.json
`"deploy": "firebase deploy --only hosting:XXXXX"`

## Sample functions
* https://github.com/domgaulton/functions-samples/tree/master/github-to-slack

## Firebase and Axios
```
const functions = require('firebase-functions');
const axios = require('axios');
const cors = require('cors')({ origin: true });
const rp = require('request-promise');

// IPify gets IP address
exports.callAPI = functions.https.onRequest((req, res) => {
  return axios.get('https://api.ipify.org?format=json')
    .then(response => {
      return postToSlack(response.data.ip);
    })
    .catch(err => {
      postToSlack(err);
    })
});

function postToSlack(message) {
  return rp({
    method: 'POST',
    // TODO: Configure the `slack.webhook_url` Google Cloud environment variables.
    uri: 'SLACK URL',
    body: {
      text: message,
    },
    json: true,
  });
}
```

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

Use `firebase functions:config:get` in project file to retrieve config data

