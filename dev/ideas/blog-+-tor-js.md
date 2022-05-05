# Blog + Tor - JS

## TODO

```
[x] server side rendering
[ ] use of gzipping and caching
[ ] detect if javascript or non-javascript user
[ ] detect if from clearnet or from tor
```

## 1. Tor

{% content-ref url="../../ict/hidden-services-aka-onion-services/setup-an-hidden-service.md" %}
[setup-an-hidden-service.md](../../ict/hidden-services-aka-onion-services/setup-an-hidden-service.md)
{% endcontent-ref %}

## 2. System Meditations

I want to use NodeJS for backend and serve only html+css pages.\
Idk anything about gzipping and caching.\
Idk what are the good practices to render pages server side.

<details>

<summary>Some sources</summary>

[https://medium.com/@baphemot/whats-server-side-rendering-and-do-i-need-it-cb42dc059b38](https://medium.com/@baphemot/whats-server-side-rendering-and-do-i-need-it-cb42dc059b38)

[https://www.digitalocean.com/community/tutorials/react-server-side-rendering](https://www.digitalocean.com/community/tutorials/react-server-side-rendering)

[https://nextjs.org/docs/basic-features/pages#two-forms-of-pre-rendering](https://nextjs.org/docs/basic-features/pages#two-forms-of-pre-rendering)

[https://www.reddit.com/r/TOR/comments/hllf94/server\_side\_rendering\_and\_noscript/](https://www.reddit.com/r/TOR/comments/hllf94/server\_side\_rendering\_and\_noscript/)

</details>

<details>

<summary>NextJS tutorial</summary>

[https://www.youtube.com/watch?v=A63UxsQsEbU\&list=PL4cUxeGkcC9g9gP2onazU5-2M-AzA8eBw](https://www.youtube.com/watch?v=A63UxsQsEbU\&list=PL4cUxeGkcC9g9gP2onazU5-2M-AzA8eBw)

</details>

### Server side html rendering (SSR) vs Static Site Generation (SSG)

These are two pre-rendering techniques.

> Imagine that we are creating a simple blog website. The content will be totally statically-generated, right? We will have only a few pages and the content will be fetched from our server, so it makes total sense to go with SSG in this case.

## 3. NextJS without client side JS

{% hint style="warning" %}
To prevent to create client side JS with NextJS, it necessary to avoid using some NextJS object like \<Link>\</Link>
{% endhint %}

{% embed url="https://www.johanbleuzen.fr/blog/next-remove-clientside-javascript" %}

{% content-ref url="broken-reference" %}
[Broken link](broken-reference)
{% endcontent-ref %}

## 3.1 Load CSS without JS

### Put CSS inside "public" directory and load them inside \_document

{% hint style="info" %}
sometimes CSS do not load, IDK why
{% endhint %}

```tsx
import Document, { Head, Html, Main, NextScript } from 'next/document'
import Navbar from '../comps/Navbar'

/* 
    The code here is available on every page
*/

function headContent() {
    return (
        <span>
            <title>Blog</title>
            <link rel="shortcut icon" href="/favicon.ico" />
            {/* 
                 HERE ! 
            */}
            <link rel="stylesheet" href="/globals.css" />
        </span>
    )
}

class HeadProduction extends Head {
    render() {
        return (
            <head {...this.props}>
                {headContent()}
            </head>
        );
    }
}

class MyDocument extends Document {
    render() {
        const isDev = process.env.NODE_ENV === "development"
        return (
            <Html>
                {isDev && <Head> {headContent()} </Head>}
                {!isDev && <HeadProduction />}
                <body>
                    <Navbar />
                    <Main />
                    {isDev && <NextScript />}
                </body>
            </Html>
        )
    }
}

export default MyDocument
```

## 4. load data server side

### getServerSideProps

```tsx
import { Component } from "react"

// 1. this gets called on every request
export async function getServerSideProps(context) {
    // const res = await fetch(`https://.../data`)
    // const data = await res.json()
    let data = { "msg": "ciao" }
    return { props: { data } }
}

// 2. called after getServerSideProps
class Home extends Component {
    render() {
        return (
            <div>
                <p> ciao </p>
                <p> {this.props['data'].msg} </p>
            </div>
        )
    }
}

export default Home
```

### from database

<details>

<summary>some sources</summary>

* [https://www.youtube.com/watch?v=FMnlyi60avU](https://www.youtube.com/watch?v=FMnlyi60avU)
*

</details>

## 5. get project in production

For example if

```
HiddenServicePort 80 127.0.0.1:8080
```

Then modify the package.json:

```json
"scripts": {
    "dev": "next",
    "build": "next build",
    "start": "next start -p 8080"     // change
},
```

Then run the scripts:

```bash
npm run build
npm run start
```
