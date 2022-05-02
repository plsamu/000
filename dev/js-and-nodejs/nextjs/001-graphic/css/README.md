# CSS

## Working CSS SSR

{% embed url="https://styled-components.com/docs/advanced#server-side-rendering" %}

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

<details>

<summary>2 - working global CSS SSR - Much better</summary>

```json
// package.json

"dependencies": {
    "next": "canary",
    "prop-types": "latest",
    "react": "latest",
    "react-dom": "latest",
    "styled-components": "latest",
    "webpack": "latest"
},
"devDependencies": {
    "@types/react": "^18.0.8",
    "babel-plugin-styled-components": "^2.0.7",
    "prettier": "latest",
    "typescript": "^4.6.4"
}
```

```
// directory tree

- public
    - favicon.ico
    - globals.css
- src
    - pages
        - _document.tsx
        - _app.tsx
        - index.tsx
```

```json
// .babelrc

{
  "presets": [
    "next/babel"
  ],
  "plugins": [
    [
      "styled-components",
      {
        "ssr": true,
        "displayName": true,
        "preprocess": false
      }
    ]
  ]
}
```

```tsx
// _document.tsx

import React from 'react';
import Document, { Head, Html, Main, NextScript } from 'next/document';
import Navbar from '../comps/Navbar'

class MyDocument extends Document {
  render() {
    console.log(this.props);
    const isDev = process.env.NODE_ENV === "development"
    return (
      <Html>
        <Head /> {/* loaded from _app */}
        <body>
          <Navbar />
          <Main />
          {isDev && <NextScript />}
        </body>
      </Html>
    )
  }
}

export default MyDocument;
```

```tsx
// _app.tsx

import React from 'react';
import Prototype from 'prop-types';
import Head from 'next/head';

const App = ({ Component }) => {

    return (
        <>
            <Head>
                <meta charSet='utf-8'></meta>
                <title>NodeBird</title>
                {/* favicon and globals are inside public dir */}
                <link rel="shortcut icon" href="/favicon.ico" />
                <link rel="stylesheet" href="/globals.css" />
            </Head>
            <Component />
        </>

    );
}

App.Prototype = {
    Component: Prototype.elementType.isRequired,
}

export default App;
```

```tsx
// index.tsx

import React from 'react'

const Index = (props) => {
  return (
    <>
      <h1>Hello World</h1>
    </>
  )
}

export default Index;
```

```css
// global.css

body {
    background-color: aquamarine;
}

h1 {
    font-size: 3rem;
    color: #ffc600;
}
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
