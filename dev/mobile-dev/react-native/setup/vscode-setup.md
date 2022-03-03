# VSCode setup

### Remember to

* rename a JavaScript file to be `*.tsx`

### Plugins

* React Native Tools
* React-Native/React/Redux snippet for es6/es7

### Fixes

```typescript
// change this
import type { Node } from 'react'
// into this
import type { ReactNode } from 'react'
```

```typescript
// change this
const App: () => Node = () => {
// into this
const App: () => ReactNode = () => {
```
