# CSS

## Client Side Javascript in DEV is necessary

{% embed url="https://nextjs.org/docs/basic-features/built-in-css-support#does-it-work-with-javascript-disabled" %}

{% embed url="https://stackoverflow.com/questions/66729498/next-js-is-not-rendering-css-in-server-side-rendering" %}

{% hint style="warning" %}
Holy fuck, doesn't work to me...\
The hell.
{% endhint %}

## Working CSS SSR

<details>

<summary>1</summary>

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
