# Fast start

### Create

```bash
npx react-native init AwesomeProject
# or
npx react-native init AwesomeProject --version X.XX.X
# or
npx react-native init AwesomeTSProject --template react-native-template-typescript
```

### Install dependencies

* [Typescript](https://reactnative.dev/docs/typescript)

### Fixes

```typescript
// change this:
import type { Node } from 'react'
// into this
import type { ReactNode } from 'react'
```

```typescript
// change this:
const App: () => Node = () => {
// into this
const App: () => ReactNode = () => {
```

### Start Metro Bundler

```
npx react-native start
```

### Start app

```bash
npx react-native run-android
```

