# 000 - create clean project

### create new project

```bash
npx create-nextjs-app proj_name
```

### delete some things

#### before

```json
"dependencies": {
    "babel-plugin-styled-components": "latest",
    "next": "canary",
    "react": "latest",
    "react-dom": "latest",
    "prop-types": "latest",
    "styled-components": "latest",
    "webpack": "latest"
},
"devDependencies": {
    "eslint": "latest",
    "babel-eslint": "latest",
    "eslint-config-airbnb": "latest",
    "eslint-config-mcansh": "latest",
    "eslint-config-prettier": "latest",
    "eslint-plugin-import": "latest",
    "eslint-plugin-jsx-a11y": "latest",
    "eslint-plugin-react": "latest",
    "eslint-plugin-prettier": "latest",
    "prettier": "latest"
  }
```

#### after

```json
"dependencies": {
    "next": "canary",
    "react": "latest"
},
"devDependencies": {
    "prettier": "latest",  // actually you can delete everything
}
```

### Install typescript

```
npm install --save-dev typescript @types/react
```

### clean

* delete everything inside `/pages`
* create `index.tsx`
* delete .babelrc file
* delete .eslint file
* delete config.js
* delete next-env.d.ts
* delete components directory

<details>

<summary>vscode some shortcuts</summary>

```kotlin
/* 
    File -> Preferences -> Keybindings
    ctrl ù              line comment
    maiusc alt a        block comment
    maiusc alt f        format page
*/
```

</details>

#### index.tsx

```tsx
import { Component } from "react";

class Home extends Component {
    state = {};
    render() {
        return (
            <p>
                Hi!
            </p>
        )
    }
}

export default Home;
```

### create \_document.tsx

{% embed url="https://www.johanbleuzen.fr/blog/next-remove-clientside-javascript" %}

The code here is available on every page.\
It's called "global file".

{% hint style="info" %}
Head and NextScript are used for performace during dev phase.\
\
Just try:\
\
npm run build\
npm run start
{% endhint %}

```tsx
import Document, { Head, Html, Main, NextScript } from 'next/document'

/* 
    The code here is available on every page
*/

class HeadProduction extends Head {
    render() {
        return (
            <head {...this.props}>
                <title>Blog</title>
            </head>
        );
    }
}

class MyDocument extends Document {
    render() {
        const isDev = process.env.NODE_ENV === "development"
        return (
            <Html>
                {isDev ? <Head /> : <HeadProduction />}
                <body>
                    <Main />
                    {isDev && <NextScript />}
                </body>
            </Html>
        )
    }
}

export default MyDocument
```

### minimalistic init mode

```
project
    - .next
    - node_modules
    - pages
        - _document.tsx
        - index.tsx
    - package-lock.json
    - package.json
    - tsconfig.json
```

### start

```
npm install
npx next telemetry disable
npm run dev
```
