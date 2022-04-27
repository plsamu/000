# NextJS

{% embed url="https://www.youtube.com/watch?list=PL4cUxeGkcC9g9gP2onazU5-2M-AzA8eBw&v=A63UxsQsEbU" %}
My beloved Net Ninja
{% endembed %}

### create new project

```bash
npx create-nextjs-app proj_name
```

### first fix - devDependencies

```
node -v
v16.14.2

npm -v
8.5.0
```

Change devDependencies

```
babel-eslint is now @babel/eslint-parser
eslint-config-mcansh is now a scoped package @mcansh/eslint-config
```

#### before

```json
"devDependencies": {
    "eslint": "latest",
    "babel-eslint": "latest",                // change
    "eslint-config-airbnb": "latest",
    "eslint-config-mcansh": "latest",        // change
    "eslint-config-prettier": "latest",
    "eslint-plugin-import": "latest",
    "eslint-plugin-jsx-a11y": "latest",
    "eslint-plugin-react": "latest",
    "eslint-plugin-prettier": "latest",
    "prettier": "latest"
  }pac
```

#### after

```json
"devDependencies": {
    "eslint": "latest",
    "@babel/eslint-parser": "latest",
    "@mcansh/eslint-config": "latest",
    "eslint-config-airbnb": "latest",
    "eslint-config-prettier": "latest",
    "eslint-plugin-import": "latest",
    "eslint-plugin-jsx-a11y": "latest",
    "eslint-plugin-react": "latest",
    "eslint-plugin-prettier": "latest",
    "prettier": "latest"
  }
```

### second fix - injectGlobal

{% embed url="https://styled-components.com/docs/faqs#what-do-i-need-to-do-to-migrate-to-v4" %}

#### before

```javascript
import { ThemeProvider, injectGlobal } from 'styled-components';

injectGlobal`
  body {
    font-family: system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI', 'Roboto', 'Oxygen', 'Ubuntu', 'Cantarell', 'Fira Sans', 'Droid Sans', 'Helvetica Neue', sans-serif, 'Apple Color Emoji', 'Segoe UI Emoji', 'Segoe UI Symbol';
  }
`;
```

#### after

```javascript
import { ThemeProvider, createGlobalStyle } from 'styled-components';

const GlobalStyle = createGlobalStyle`
  body {
    font-family: system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI', 'Roboto', 'Oxygen', 'Ubuntu', 'Cantarell', 'Fira Sans', 'Droid Sans', 'Helvetica Neue', sans-serif, 'Apple Color Emoji', 'Segoe UI Emoji', 'Segoe UI Symbol';
  }
`;
```

```
npm install
npx next telemetry disable
npm run dev
```
