# NO JS

{% embed url="https://www.johanbleuzen.fr/blog/next-remove-clientside-javascript" %}

{% embed url="https://stackoverflow.com/a/59201411/16988820" %}

```tsx
// _app.tsx

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

```tsx
// _document.tsx

import React from "react";
import Document, { Head, Html, Main, NextScript } from "next/document";

export default class MyDocument extends Document {
  render() {
    const isDev = process.env.NODE_ENV === "development"
    return (
        <Html>
            <Head /> 
            <body>
              {isDev && <Main />}
              {isDev && <NextScript />}
            </body>
        </Html>
    )    
  }
}
```
