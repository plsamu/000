# React.Context - Global data

## Example 1 - Context in \_app.js

```
lib
    AppContext.tsx
src
    api
        quotes.json
    components
    containers
    pages
        _app.tsx
        index.tsx
public
```

```tsx
// AppContext
import React from "react";
const AppContext = React.createContext({});
export default AppContext;
```

#### `quotes.json`

```json
[
    {
        "quote": "Goodbye World!",
        "author": "Elon Musk"
    }
]
```

```tsx
// _app.tsx
import React from "react";
import AppContext from "../../lib/AppContext";

// load data from json 
import Quotes from "../api/quotes.json";

const App = ({ Component, pageProps }) => {
  return (
    <>
      <AppContext.Provider value={{ Quotes }}>
        <Component {...pageProps} />
      </AppContext.Provider>
    </>
  );
};a
```

```tsx
// index.tsx
import { Component, useContext } from "react";
import Head from "next/head";
import AppContext from "../../lib/AppContext";

class Home extends Component {
  render() {
    const value = useContext(AppContext);
    console.log(value);
    return (
      <>
        <Head>
          <title>Home</title>
        </Head>
      </>
    );
  }
}

export default Home;
```









