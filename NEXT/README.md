This is a [Next.js](https://nextjs.org/) project bootstrapped with [`create-next-app`](https://github.com/vercel/next.js/tree/canary/packages/create-next-app).

## Getting Started

First, run the development server:

```bash
npm run dev
# or
yarn dev
```

Open [http://localhost:3000](http://localhost:3000) with your browser to see the result.

You can start editing the page by modifying `pages/index.js`. The page auto-updates as you edit the file.

[API routes](https://nextjs.org/docs/api-routes/introduction) can be accessed on [http://localhost:3000/api/hello](http://localhost:3000/api/hello). This endpoint can be edited in `pages/api/hello.js`.

The `pages/api` directory is mapped to `/api/*`. Files in this directory are treated as [API routes](https://nextjs.org/docs/api-routes/introduction) instead of React pages.

## Learn More

To learn more about Next.js, take a look at the following resources:

- [Next.js Documentation](https://nextjs.org/docs) - learn about Next.js features and API.
- [Learn Next.js](https://nextjs.org/learn) - an interactive Next.js tutorial.

You can check out [the Next.js GitHub repository](https://github.com/vercel/next.js/) - your feedback and contributions are welcome!

## Deploy on Vercel

The easiest way to deploy your Next.js app is to use the [Vercel Platform](https://vercel.com/new?utm_medium=default-template&filter=next.js&utm_source=create-next-app&utm_campaign=create-next-app-readme) from the creators of Next.js.

Check out our [Next.js deployment documentation](https://nextjs.org/docs/deployment) for more details.

## Tutorial
- Youtube https://www.youtube.com/watch?v=mTz0GXj8NN0
- Initial Codebase `npx create-next-app next-crash-course`
- Final Codebase - https://github.com/bradtraversy/next-crash-course
- GraphQL + Fetch https://www.freecodecamp.org/news/how-to-fetch-graphql-data-in-next-js-with-apollo-graphql/

## Learning

### Public Folder
Directly accessible by the browser

### Pages Folder

#### Standard
* `_app.js` - Wraps around all of the page components and returns `pageProps`. Where you would include Nav Footer etc
* `index.js` - homepage (main route). Adding new pages e.g. about.js would create about us page. You can't import global style sheets into components.

#### Custom Document
* `_document.js` - Allows you to overwrite meta tags for each individual page.
```js
static async getInitialProps(ctx) {
  const initialProps = await Document.getInitialProps(ctx)
  return { ...initialProps }
}
```

### Components Folder
Used for components that won't have a route
* Uppercase for components. Can import style.module.css

### CSS / Modules
* css.modules can only be imported to route pages e.g. `index.js` without the underscore
```js
const x = 5;
<style jsx>
  {`
    .title {
      color: ${x > 3 ? 'red' : 'blue'};
    }
  `}
</style>
```

### Imports
* e.g. `import X from 'next/xxx'`

### Routing and nested routes
Use pages folder and structure like a standard folder structure e.g. `/articles/[id].js` where `articles` and `[id]` are folders and in the `[id]` folder is a file names `index.js`. See `Router (next/router)` below

#### Router (next/router)
* `import { useRouter } from 'next/router';`

**Option 1**
* `const router = useRouter();` - contains any parameters that exist in the route e.g. `[id]`
* `const { id } = router.query` - query the route with the parameter. You then have access to `id` in the render

**Option 2 (Recommended)**
* See `getServerSideProps` below.

#### Link (next/link)
* `import Link from 'next/link';`
* Use `href` like you would on `<a href"">`

#### Head (next/head) - Also see `Custom Document`
* `import Head from 'next/head';`
* Used for meta and important for SEO

#### Document (next/document)
* `import Document, { Html, Head, Main, NextScript } from 'next/document'`

### Custom Meta Component
Create a custom `<head>` section as `Meta.js` in the components folder and import it at the top of your layout (not `_document.js` or `index.js`).   
```js
import Head from 'next/head'

const Meta = ({ title, keywords, description }) => {
  return (
    <Head>
      <meta name='viewport' content='width=device-width, initial-scale=1' />
      <meta name='keywords' content={keywords} />
      <meta name='description' content={description} />
      <meta charSet='utf-8' />
      <link rel='icon' href='/favicon.ico' />
      <title>{title}</title>
    </Head>
  )
}

Meta.defaultProps = {
  title: 'WebDev Newz',
  keywords: 'web development, programming',
  description: 'Get the latest news in web dev',
}

export default Meta
```
To use this on a specific page you can import Meta and pass title, keywords, description as props.

### Using Data

#### Fetch Data
Within `index.js` there are three functions we can use to fetch data

##### getStaticProps
Fetch a build time and pass to the render function `export default function Home({data}) {`
```js
export const getStaticProps = async () => {
  const res = await.fetch(`https://jsonplaceholder.typicode.com/posts?_limit=6`);
  const data = await res.json()

  // add data to the props (destructed data: data)
  return {
    props: {
      data,
    }
  }
}
````

#### getServerSideProps
Fetch data on request time when you hit a url specific to the data
* `context` is the context of the url
```js
export const getServerSideProps = async (context) => {
  const client = new ApolloClient({
    uri: 'https://graphqlzero.almansi.me/api',
    cache: new InMemoryCache()
  });

  const { data } = await client.query({
    query: gql`
      query {
        post(id: ${context.params.id}) {
          id
          title
          body
        }
      }
    `
  });

  return {
    props: {
      data: data,
    }
  }
}
````

#### getStaticPaths
Create paths based on data we're fetching. Good for sitemaps? Used in conjunction with getStaticProps
* How we want this data returned is as follows;
```js
return {
  paths: {params: {id: '1', id: '2', id: '3'}}
}
```

Function looks like this
```js
// Get data from api call
export const getStaticProps = async (context) => {
  const client = new ApolloClient({
    uri: 'https://graphqlzero.almansi.me/api',
    cache: new InMemoryCache()
  });

  const { data } = await client.query({
    query: gql`
      query {
        post(id: ${context.params.id}) {
          id
          title
          body
        }
      }
    `
  });

  return {
    props: {
      data: data,
    }
  }
}

// Generate all the paths on the server
export const getStaticPaths = async () => {
  const client = new ApolloClient({
    uri: 'https://graphqlzero.almansi.me/api',
    cache: new InMemoryCache()
  });

  const { data } = await client.query({
    query: gql`
      query (
        $options: PageQueryOptions
      ) {
        posts(options: $options) {
          data {
            id
            title
          }
          meta {
            totalCount
          }
        }
      }
    `
  });

  // Get ids from the posts and create an array
  const ids = data.posts.data.map(d => d.id);

  // Loop over array and create the paths object like `{params: {id: '1', id: '2', id: '3'}}`
  const paths = ids.map(id => ({ params: {id: id.toString()} }));
  
  // fallback: false means if we go to something that doesn't exist we go to a 404 page
  return {
    paths,
    fallback: false
  }
}
```

### Using Graph QL 
See - https://graphqlzero.almansi.me/
See - https://graphqlzero.almansi.me/api

Import using `import { ApolloClient, InMemoryCache, gql } from '@apollo/client';`

Query data using the below
```js
const client = new ApolloClient({
  uri: 'https://graphqlzero.almansi.me/api',
  cache: new InMemoryCache()
});

const { data } = await client.query({
  query: gql`
    query (
      $options: PageQueryOptions
    ) {
      posts(options: $options) {
        data {
          id
          title
        }
        meta {
          totalCount
        }
      }
    }
  `
});

return {
  props: {
    data,
  }
}
```

### Deploying

#### Static Site 
Create html pages based on imported data to add to a server
* Run `next export` to do so. This can be added as a script to package.json e.g. `npm run export`
* Creates an `/out` folder with a static website 

### API Routes
Similar to express js - backend rest API. Allows users on your site to make API calls.
Use code below within `/api/xxxx/index.js` to import data and then return api call with 200 (okay status). If you hit the url `/api/xxxx` you will see the data.
Useful if you want to query your own database and then set up pages and routes.
```js
import { articles } from '../../../data.js';

export default function handler(req, res) {
  res.status(200).json(articles);
}
```
If looking for a specific api route e.g. `/api/xxxx/[id]` create a file called `[id].js` within the `xxxx` folder and go to the url `/api/xxxx/X` to see the repsonse.
```js
import { articles } from '../../../data.js';

export default function handler(req, res) {
  const articleId = req.query.id;
  const filtered = articles.filter(article => article.id === articleId);
  if ( filtered.length > 0 ) {
    // send the response
    res.status(200).json(filtered[0]);
  } else {
    // filtered not found send 404
    res.status(404).json({message: `id ${articleId} not found`});
  } 
}
```