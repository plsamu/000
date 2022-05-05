# styled-components - createGlobalStyle - injectGlobal

{% hint style="danger" %}
`injectGlobal` was changed for `createGlobalStyle`
{% endhint %}

{% hint style="info" %}
Heuristics:\
to use styled-components without Javascript, meaning in SSR mode, ServerStyleSheet must be used.
{% endhint %}

{% embed url="https://styled-components.com/docs/advanced#server-side-rendering" %}

## createGlobalStyle

{% hint style="warning" %}
Use Javascript to load CSS.
{% endhint %}

```kotlin
import React from "react";
import Head from "next/head";
import styled from "styled-components";
import theme from '../config';
import { createGlobalStyle } from "styled-components";

const GlobalStyles = createGlobalStyle`
body {
  background: yellow;
}
`;

const Title = styled.h1`
  font-size: 3rem;
`;

const Index = () => (
  <>
    <Head>
      <meta charSet="utf-8"></meta>
      <title>NodeBird</title>
      {/* favicon is inside public dir */}
      <link rel="shortcut icon" href="/favicon.ico" />
    </Head>
    <GlobalStyles />
    <Title>Hello World</Title>
  </>
);

export default Index;
```
