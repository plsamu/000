# CSS

## Inline load

```tsx
export function Button() {
  return (
    <button
      type="button"
        style={{
            color: 'white',
            backgroundColor: 'red'
        }}
    >
      Btn1
    </button>
  )
}
```

## Component load

```tsx
 <>
    <div className="main"> Halpp </div>
    
    <style jsx>{`
    .main {
        background: green;
    }
    `}</style>
</>
```

## Global load

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
                <title>title</title>
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

## Document (\_document) load

The code here is available on every page. In theory.

```tsx
import Document, { Head, Html, Main, NextScript } from 'next/document'
import Navbar from '../comps/Navbar'

function headContent() {
    return <Head>
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
        </Head>
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

## App (\_app) load

```tsx
import React from "react";
import Head from "next/head";

const App = ({ Component, pageProps }) => {
  return (
    <>
      <Head>
        <meta charSet="utf-8"></meta>
        <title>NodeBird</title>
        {/* favicon and globals are inside public dir */}
        <link rel="shortcut icon" href="/favicon.ico" />
        <link rel="stylesheet" href="/globals.css" />
      </Head>
      <Component {...pageProps} />
    </>
  );
};

export default App;
```
