# Webflow

## API

### General Info

```curl
$ curl https://api.webflow.com/info \
  -H "Authorization: Bearer {API KEY}" \
  -H 'accept-version: 1.0.0'
```

```json
{
   "_id":"5f86de76a7294c3c83eaaa14",
   "createdOn":"2020-10-14T11:18:14.772Z",
   "grantType":"client_credentials",
   "lastUsed":"2020-10-14T11:18:39.451Z",
   "sites":[
      "5f7318268aa95711a570d244"
   ],
   "orgs":[
      
   ],
   "users":[
      
   ],
   "rateLimit":60,
   "status":"confirmed"
}
```

### General Sites Info

```curl
$ curl https://api.webflow.com/sites \
  -H "Authorization: Bearer {API KEY}" \
  -H 'accept-version: 1.0.0'
```

```json
[
   {
      "_id":"5f7318268aa95711a570d244",
      "createdOn":"2020-09-29T11:19:02.137Z",
      "name":"Future Ford",
      "shortName":"future-ford",
      "lastPublished":"2020-10-14T11:14:55.099Z",
      "previewUrl":"https://screenshots.webflow.com/sites/5f7318268aa95711a570d244/20201014111455_119a04cc80006e863d0e0729b7eff78f.png",
      "timezone":"Europe/Lisbon",
      "database":"5f743a82556750082706b655"
   }
]
```

### Specific Sites Info

```curl
$ curl https://api.webflow.com/sites/5f7318268aa95711a570d244 \
    -H "Authorization: Bearer {API KEY}" \
    -H 'accept-version: 1.0.0'
```

```json
{
   "_id":"5f7318268aa95711a570d244",
   "createdOn":"2020-09-29T11:19:02.137Z",
   "name":"Future Ford",
   "shortName":"future-ford",
   "lastPublished":"2020-10-14T11:14:55.099Z",
   "previewUrl":"https://screenshots.webflow.com/sites/5f7318268aa95711a570d244/20201014111455_119a04cc80006e863d0e0729b7eff78f.png",
   "timezone":"Europe/Lisbon",
   "database":"5f743a82556750082706b655"
}
```

### Publish

```curl
$ curl https://api.webflow.com/sites/5f7318268aa95711a570d244/publish \
    -H "Authorization: Bearer {API KEY}" \
    -H 'accept-version: 1.0.0' \
    -H "Content-Type: application/json" \
    --data-binary $'{
      "domains": ["future-ford.webflow.io"]
    }'
```

```json
{"queued":true} 
```

### Collections

```curl
$ curl https://api.webflow.com/sites/5f7318268aa95711a570d244/collections \
    -H "Authorization: Bearer {API KEY}" \
    -H 'accept-version: 1.0.0'
```

```json
[
   {
      "_id":"5f743d176aba26246bbadf6a",
      "lastUpdated":"2020-10-05T15:13:18.996Z",
      "createdOn":"2020-09-30T08:08:55.476Z",
      "name":"Articles",
      "slug":"articles",
      "singularName":"Article"
   },
   {
      "_id":"5f743a839fd12a5c9e341c71",
      "lastUpdated":"2020-10-02T14:39:09.928Z",
      "createdOn":"2020-09-30T07:57:55.246Z",
      "name":"Categories",
      "slug":"categories",
      "singularName":"Category"
   }
]
```

### All Collection Items

```curl
$ curl https://api.webflow.com/collections/5f743d176aba26246bbadf6a/items?limit=5\
    -H "Authorization: Bearer {API KEY}" \
    -H 'accept-version: 1.0.0'
```

```json
{
   "items":[
      {
         "video":{
            "url":"https://www.youtube.com/watch?v=FwwIYdB_wic&ab_channel=AwwNetwork",
            "metadata":{
               "width":854,
               "height":480,
               "html":"<iframe class=\"embedly-embed\" src=\"//cdn.embedly.com/widgets/media.html?src=https%3A%2F%2Fwww.youtube.com%2Fembed%2FFwwIYdB_wic%3Ffeature%3Doembed&display_name=YouTube&url=https%3A%2F%2Fwww.youtube.com%2Fwatch%3Fv%3DFwwIYdB_wic&image=https%3A%2F%2Fi.ytimg.com%2Fvi%2FFwwIYdB_wic%2Fhqdefault.jpg&key=96f1f04c5f4143bcb0f2e68c87d65feb&type=text%2Fhtml&schema=youtube\" width=\"854\" height=\"480\" scrolling=\"no\" title=\"YouTube embed\" frameborder=\"0\" allow=\"autoplay; fullscreen\" allowfullscreen=\"true\"></iframe>",
               "aspectRatio":0,
               "title":"Sheep Discovers How To Use A Trampoline",
               "provider_name":"YouTube",
               "type":"video",
               "thumbnail_url":"https://i.ytimg.com/vi/FwwIYdB_wic/hqdefault.jpg",
               "description":"For more content like this be sure to like and subscribe! Also, Comment any other animal content you'd like to see and I'll be sure to post some! Sheep Disco...",
               "author_name":"Aww Network"
            }
         },
         "_archived":false,
         "_draft":false,
         "name":"The process of creating the ford ",
         "slug":"the-process-of-creating-the-ford",
         "image":{
            "fileId":"5f85b2fd10debb2e9824746c",
            "url":"https://uploads-ssl.webflow.com/5f743a82556750082706b655/5f85b2fd10debb2e9824746c_cq5dam.web_.881.495.jpeg",
            "alt":null
         },
         "category":"5f743a8c34fb14006afda10d",
         "updated-on":"2020-10-14T14:14:37.004Z",
         "updated-by":"Person_5f2d6e49155e952c95768aa0",
         "created-on":"2020-10-13T14:00:35.474Z",
         "created-by":"Collaborator_5f734e5000249e3cf3c9e375",
         "published-on":"2020-10-14T14:18:32.413Z",
         "published-by":"Person_5f2d6e49155e952c95768aa0",
         "display-title-on-article-page":true,
         "_cid":"5f743d176aba26246bbadf6a",
         "_id":"5f85b3031b2284f65854328a"
      },
      {
         "_archived":false,
         "_draft":false,
         "article-content":"<p>Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.</p>",
         "name":"Delve into the electric cars architecture",
         "intro":"Excepteur sint occaecat ",
         "article-summary":"<p><strong>Delve into the electric cars architecture</strong></p><p><em>Excepteur sin</em>t occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.</p><p>‍</p>",
         "slug":"delve-into-the-electric-cars-architecture",
         "image":{
            "fileId":"5f85b1e7789efc56debe0618",
            "url":"https://uploads-ssl.webflow.com/5f743a82556750082706b655/5f85b1e7789efc56debe0618_lucas-jubb-back-to-the-future-ford-gt-illustration-lucas-jubb.png",
            "alt":null
         },
         "category":"5f743a8c34fb14006afda10d",
         "updated-on":"2020-10-14T14:14:31.886Z",
         "updated-by":"Person_5f2d6e49155e952c95768aa0",
         "created-on":"2020-10-13T13:56:52.501Z",
         "created-by":"Collaborator_5f734e5000249e3cf3c9e375",
         "published-on":"2020-10-14T14:18:32.413Z",
         "published-by":"Person_5f2d6e49155e952c95768aa0",
         "display-title-on-article-page":true,
         "_cid":"5f743d176aba26246bbadf6a",
         "_id":"5f85b224ef2b4d1a1c97796e"
      },
      {
         "_archived":false,
         "_draft":false,
         "article-content":"<p>Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.</p><p>Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.</p><p><a href=\"https://google.com\">Lorem ipsum dolor sit amet</a>, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.</p>",
         "name":"The future is ford the future is now",
         "intro":"Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore ",
         "read-more-text":"Learn about lorem ipsum",
         "article-summary":"<p>Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.</p>",
         "image":{
            "fileId":"5f85aeb190caed00c7ecfbb8",
            "url":"https://uploads-ssl.webflow.com/5f743a82556750082706b655/5f85aeb190caed00c7ecfbb8_46a38ce0-ford-ranger.jpg",
            "alt":null
         },
         "slug":"the-future-is-ford-the-future-is-now",
         "category":"5f743a8c34fb14006afda10d",
         "updated-on":"2020-10-14T13:42:35.263Z",
         "updated-by":"Person_5f2d6e49155e952c95768aa0",
         "created-on":"2020-10-13T13:43:43.387Z",
         "created-by":"Collaborator_5f734e5000249e3cf3c9e375",
         "published-on":"2020-10-14T13:43:01.906Z",
         "published-by":"Person_5f2d6e49155e952c95768aa0",
         "display-title-on-article-page":true,
         "_cid":"5f743d176aba26246bbadf6a",
         "_id":"5f85af0fcc388a734c0bfdda"
      },
      {
         "_archived":false,
         "_draft":false,
         "article-content":"<p><strong>Lorem ipsum dolor sit amet</strong>, <em>consectetur adipiscing elit</em>, <a href=\"https://google.com\">sed do eiusmod tempor incididunt</a> ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.</p><ul><li>Lorem ipsum dolor sit amet, consectetur adipiscing elit</li><li>Sed do eiusmod tempor incididunt ut labore et dolore magna aliqua </li><li>Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat</li><li>Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur</li></ul><p>Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.</p><figure class=\"w-richtext-figure-type-image w-richtext-align-fullwidth\" style=\"max-width:660px\"><div><img src=\"https://uploads-ssl.webflow.com/5f743a82556750082706b655/5f7f28f58d825381094207f9_MW-HC120_ford12_20190116125049_ZQ.jpg\" loading=\"lazy\" width=\"auto\" height=\"auto\"></div></figure><p><strong>Lorem ipsum dolor sit amet</strong>, <em>consectetur adipiscing elit</em>, <a href=\"https://google.com\">sed do eiusmod tempor incididunt</a> ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.</p><figure class=\"w-richtext-figure-type-image w-richtext-align-fullwidth\" style=\"max-width:2000px\"><div><img src=\"https://uploads-ssl.webflow.com/5f743a82556750082706b655/5f7f3020d296bfaa0f6af961_puma-st-large-banner-1.png\" loading=\"lazy\"></div></figure>",
         "name":"Excepteur sint occaecat cupidatat non proident sunt in culpa",
         "intro":"Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore",
         "read-more-text":"Find out what we have to offer",
         "article-summary":"<h5>Lorem ipsum dolor sit amet</h5><p>Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.</p>",
         "slug":"excepteur-sint-occaecat-cupidatat-non-proident-sunt-in-culpa",
         "image":{
            "fileId":"5f7f289b9ce877304c6f34bd",
            "url":"https://uploads-ssl.webflow.com/5f743a82556750082706b655/5f7f289b9ce877304c6f34bd_stock-Ford-SUV-01-company.jpg",
            "alt":null
         },
         "category":"5f743a8c34fb14006afda10d",
         "updated-on":"2020-10-14T14:14:42.655Z",
         "updated-by":"Person_5f2d6e49155e952c95768aa0",
         "created-on":"2020-10-08T14:59:11.823Z",
         "created-by":"Collaborator_5f734e5000249e3cf3c9e375",
         "published-on":"2020-10-14T14:18:32.413Z",
         "published-by":"Person_5f2d6e49155e952c95768aa0",
         "display-title-on-article-page":true,
         "_cid":"5f743d176aba26246bbadf6a",
         "_id":"5f7f293ff2c4c7ee4f52d7db"
      },
      {
         "_archived":false,
         "_draft":false,
         "name":"Future Winning Article",
         "intro":"Future winning article intro copy here. This is a place to introduce the article",
         "read-more-text":"Add some click bait here...",
         "article-summary":"<h2>Liked this?</h2><p>You'll love Nullam iaculis molestie magna, a iaculis nisl sagittis et. Sed non ornare purus. Duis sed mauris fermentum, aliquam eros in, tincidunt felis. Fusce molestie, erat in rhoncus auctor, magna dui mattis dolor, eget eleifend neque lacus eu ante. In finibus fringilla diam.</p>",
         "slug":"future-winning-article",
         "image":{
            "fileId":"5f7741d001162c304978e283",
            "url":"https://uploads-ssl.webflow.com/5f743a82556750082706b655/5f7741d001162c304978e283_jason-dent-WNVGLwGMCAg-unsplash.jpg",
            "alt":null
         },
         "category":"5f743a8c34fb14006afda10d",
         "updated-on":"2020-10-14T14:14:46.104Z",
         "updated-by":"Person_5f2d6e49155e952c95768aa0",
         "created-on":"2020-10-02T15:05:27.481Z",
         "created-by":"Person_5f2d6e49155e952c95768aa0",
         "published-on":"2020-10-14T14:18:32.413Z",
         "published-by":"Person_5f2d6e49155e952c95768aa0",
         "article-content":"<h2>Et quasi temporibus ut aliquam dolores ut itaque laboriosam omnis.</h2><p>Aut quae magnam omnis beatae tempore quia. Rem sit iusto expedita nostrum reprehenderit ut libero. Sit quod saepe quisquam laborum quia velit in. Facilis expedita vel eaque aut vitae natus autem.</p><figure class=\"w-richtext-figure-type-image w-richtext-align-center\"><div><img src=\"https://uploads-ssl.webflow.com/5f743a82556750082706b655/5f7741d001162c304978e283_jason-dent-WNVGLwGMCAg-unsplash.jpg\" loading=\"lazy\"></div></figure><h3>Voluptatum reprehenderit assumenda quis saepe voluptatem quam praesentium nesciunt natus.</h3><figure class=\"w-richtext-figure-type-video w-richtext-align-center\" style=\"padding-bottom:33.723653395784545%\"><div><iframe allowfullscreen=\"true\" frameborder=\"0\" scrolling=\"no\" src=\"https://www.youtube.com/embed/4-7jBLqSlzg\"></iframe></div></figure><blockquote>Est debitis ut et praesentium culpa est aut modi et. Quia repudiandae aperiam dolorum expedita aperiam. Repellendus praesentium beatae autem quasi omnis architecto ratione rerum distinctio.</blockquote><ul><li>List one</li><li>list item 2</li></ul><h1>Lists</h1><p><a href=\"https://www.youtube.com/watch?v=4-7jBLqSlzg\" target=\"_blank\">Click here</a></p><ol start=\"\"><li>order list</li><li>ordering shopping</li><li>order anything</li></ol><p>Eligendi at ipsa suscipit necessitatibus harum aliquid sint. Autem natus eum iusto reprehenderit facilis nam. Temporibus minus porro est sed molestiae. Optio accusamus exercitationem ad qui.</p><p>Provident odit totam saepe itaque praesentium aut molestiae. Asperiores ut excepturi. Rerum optio non voluptatem neque dolor et cum.</p><p>‍</p>",
         "display-title-on-article-page":true,
         "_cid":"5f743d176aba26246bbadf6a",
         "_id":"5f7741b7a0241060df049344"
      }
   ],
   "count":5,
   "limit":5,
   "offset":0,
   "total":12
}
```

### Patch an item
* Note the `?live=true` on live flag if it appears on live already

```curl
$ curl -X PATCH 'https://api.webflow.com/collections/5f743d176aba26246bbadf6a/items/5f86ea0e7911867b1770fc1d?live=true' \
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
{
   "_archived":false,
   "_draft":false,
   "article-content":"<p>content</p>",
   "name":"something to test",
   "intro":"Intro text from api auto update",
   "read-more-text":"Read more",
   "image":{
      "fileId":"5f86ea03cee6a4342a3077b6",
      "url":"https://uploads-ssl.webflow.com/5f743a82556750082706b655/5f86ea03cee6a4342a3077b6_fiber_555x650_0.jpg",
      "alt":null
   },
   "slug":"something-to-test",
   "category":"5f743a8c01690c70cf2cc339",
   "updated-on":"2020-10-14T12:15:25.821Z",
   "updated-by":"Person_5f2d6e49155e952c95768aa0",
   "created-on":"2020-10-14T12:07:42.807Z",
   "created-by":"Person_5f2d6e49155e952c95768aa0",
   "published-on":"2020-10-14T12:15:25.821Z",
   "published-by":"Person_5f2d6e49155e952c95768aa0",
   "_cid":"5f743d176aba26246bbadf6a",
   "_id":"5f86ea0e7911867b1770fc1d"
}
```