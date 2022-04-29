# CSS

## Working CSS SSR

<details>

<summary>1 - first working method, I hate this</summary>

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
            <style>{`
                p {
                    color: blue;
                }
                div {
                    background: red;
                }
                @media (max-width: 600px) {
                    div {
                        background: blue;
                    }
                }
            `}</style>
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

</details>

## Sources

{% embed url="https://medium.com/swlh/server-side-rendering-styled-components-with-nextjs-1db1353e915e" %}

{% embed url="https://jsramblings.com/server-side-rendered-styled-components-with-nextjs" %}

{% embed url="https://www.youtube.com/watch?v=3eUZeuGXo_U" %}

## Client Side Javascript in DEV is necessary

{% hint style="warning" %}
Holy fuck, doesn't work to me...\
The hell.
{% endhint %}

{% embed url="https://nextjs.org/docs/basic-features/built-in-css-support#does-it-work-with-javascript-disabled" %}

{% embed url="https://stackoverflow.com/questions/66729498/next-js-is-not-rendering-css-in-server-side-rendering" %}
