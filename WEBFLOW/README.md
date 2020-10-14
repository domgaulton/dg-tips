# Webflow

## API

### General Info

```curl
curl https://api.webflow.com/info \
  -H "Authorization: Bearer {API KEY}" \
  -H 'accept-version: 1.0.0'
```

```json
{"_id":"5f86de76a7294c3c83eaaa14","createdOn":"2020-10-14T11:18:14.772Z","grantType":"client_credentials","lastUsed":"2020-10-14T11:18:39.451Z","sites":["5f7318268aa95711a570d244"],"orgs":[],"users":[],"rateLimit":60,"status":"confirmed"}
```

### General Sites Info

```curl
curl https://api.webflow.com/sites \
  -H "Authorization: Bearer {API KEY}" \
  -H 'accept-version: 1.0.0'
```

```json
[{"_id":"5f7318268aa95711a570d244","createdOn":"2020-09-29T11:19:02.137Z","name":"Future Ford","shortName":"future-ford","lastPublished":"2020-10-14T11:14:55.099Z","previewUrl":"https://screenshots.webflow.com/sites/5f7318268aa95711a570d244/20201014111455_119a04cc80006e863d0e0729b7eff78f.png","timezone":"Europe/Lisbon","database":"5f743a82556750082706b655"}]
```

### Specific Sites Info

```curl
curl https://api.webflow.com/sites/5f7318268aa95711a570d244 \
    -H "Authorization: Bearer {API KEY}" \
    -H 'accept-version: 1.0.0'
```

```json
{"_id":"5f7318268aa95711a570d244","createdOn":"2020-09-29T11:19:02.137Z","name":"Future Ford","shortName":"future-ford","lastPublished":"2020-10-14T11:14:55.099Z","previewUrl":"https://screenshots.webflow.com/sites/5f7318268aa95711a570d244/20201014111455_119a04cc80006e863d0e0729b7eff78f.png","timezone":"Europe/Lisbon","database":"5f743a82556750082706b655"}
```

### Publish

```curl
curl https://api.webflow.com/sites/5f7318268aa95711a570d244/publish \
    -H "Authorization: Bearer {API KEY}" \
    -H 'accept-version: 1.0.0' \
    -H "Content-Type: application/json" \
    --data-binary $'{
      "domains": ["future-ford.webflow.io"]
    }'
```

```json
Returns // {"queued":true} 
```

### Collections

```curl
curl https://api.webflow.com/sites/5f7318268aa95711a570d244/collections \
    -H "Authorization: Bearer {API KEY}" \
    -H 'accept-version: 1.0.0'
```

```json
[{"_id":"5f743d176aba26246bbadf6a","lastUpdated":"2020-10-05T15:13:18.996Z","createdOn":"2020-09-30T08:08:55.476Z","name":"Articles","slug":"articles","singularName":"Article"},{"_id":"5f743a839fd12a5c9e341c71","lastUpdated":"2020-10-02T14:39:09.928Z","createdOn":"2020-09-30T07:57:55.246Z","name":"Categories","slug":"categories","singularName":"Category"}]
```

### All Collection Items

```curl
curl https://api.webflow.com/collections/5f743d176aba26246bbadf6a/items?limit=1\
    -H "Authorization: Bearer {API KEY}" \
    -H 'accept-version: 1.0.0'
```

```json
{"items":[{"video":{"url":"https://www.youtube.com/watch?v=FwwIYdB_wic&ab_channel=AwwNetwork","metadata":{"width":854,"height":480,"html":"<iframe class=\"embedly-embed\" src=\"//cdn.embedly.com/widgets/media.html?src=https%3A%2F%2Fwww.youtube.com%2Fembed%2FFwwIYdB_wic%3Ffeature%3Doembed&display_name=YouTube&url=https%3A%2F%2Fwww.youtube.com%2Fwatch%3Fv%3DFwwIYdB_wic&image=https%3A%2F%2Fi.ytimg.com%2Fvi%2FFwwIYdB_wic%2Fhqdefault.jpg&key=96f1f04c5f4143bcb0f2e68c87d65feb&type=text%2Fhtml&schema=youtube\" width=\"854\" height=\"480\" scrolling=\"no\" title=\"YouTube embed\" frameborder=\"0\" allow=\"autoplay; fullscreen\" allowfullscreen=\"true\"></iframe>","aspectRatio":0,"title":"Sheep Discovers How To Use A Trampoline","provider_name":"YouTube","type":"video","thumbnail_url":"https://i.ytimg.com/vi/FwwIYdB_wic/hqdefault.jpg","description":"For more content like this be sure to like and subscribe! Also, Comment any other animal content you'd like to see and I'll be sure to post some! Sheep Disco...","author_name":"Aww Network"}},"_archived":false,"_draft":false,"name":"The process of creating the ford ","slug":"the-process-of-creating-the-ford","image":{"fileId":"5f85b2fd10debb2e9824746c","url":"https://uploads-ssl.webflow.com/5f743a82556750082706b655/5f85b2fd10debb2e9824746c_cq5dam.web_.881.495.jpeg","alt":null},"category":"5f743a8c34fb14006afda10d","updated-on":"2020-10-13T14:00:35.474Z","updated-by":"Collaborator_5f734e5000249e3cf3c9e375","created-on":"2020-10-13T14:00:35.474Z","created-by":"Collaborator_5f734e5000249e3cf3c9e375","published-on":"2020-10-13T14:00:35.474Z","published-by":"Collaborator_5f734e5000249e3cf3c9e375","_cid":"5f743d176aba26246bbadf6a","_id":"5f85b3031b2284f65854328a"}],"count":1,"limit":1,"offset":0,"total":12}
```

### Patch an item
* Note the `?live=true` on live flag if it appears on live already
```curl
curl -X PATCH 'https://api.webflow.com/collections/5f743d176aba26246bbadf6a/items/5f86ea0e7911867b1770fc1d?live=true' \
  -H "Authorization: Bearer {API KEY}" \
  -H 'accept-version: 1.0.0' \
  -H "Content-Type: application/json" \
  --data-binary $'{
      "fields": {
        "intro":"Intro text from api auto update"
      }
    }'
```

```json
{"_archived":false,"_draft":false,"article-content":"<p>content</p>","name":"something to test","intro":"Intro text from api auto update","read-more-text":"Read more","image":{"fileId":"5f86ea03cee6a4342a3077b6","url":"https://uploads-ssl.webflow.com/5f743a82556750082706b655/5f86ea03cee6a4342a3077b6_fiber_555x650_0.jpg","alt":null},"slug":"something-to-test","category":"5f743a8c01690c70cf2cc339","updated-on":"2020-10-14T12:15:25.821Z","updated-by":"Person_5f2d6e49155e952c95768aa0","created-on":"2020-10-14T12:07:42.807Z","created-by":"Person_5f2d6e49155e952c95768aa0","published-on":"2020-10-14T12:15:25.821Z","published-by":"Person_5f2d6e49155e952c95768aa0","_cid":"5f743d176aba26246bbadf6a","_id":"5f86ea0e7911867b1770fc1d"}
```