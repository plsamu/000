# Setup

## Fast Start

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

### Start Metro Bundler

```
npx react-native start
```

### Start app

```bash
npx react-native run-android
```

## Basics

* Babel is a **free** and **open-source** JavaScript **transpiler**. A transpiler (source-to-source compilers) is a tool that reads source code which is written in one programming language and produces the equivalent code in another _programming language_.
* TypeScript is an **open-source** pure **object-oriented** programing language. It is a strongly typed **superset** of JavaScript which compiles to plain JavaScript.
* import React from "react": deals with logic.
* import { ... } from "react-native": deals with graphics.

## VSCode Setup



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

