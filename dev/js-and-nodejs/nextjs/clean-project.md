# Clean project

```
npx create-nextjs-app proj_name
```

```json
"dependencies": {
    "next": "canary",
    "react": "latest"
}
```

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
* move components and pages dirs inside src

### src

```
project
    - .next
    - node_modules
    - src
        - components
        - styles (dynamic, likely use js)
        - pages
            - _document.tsx
            - index.tsx
    - public
        - styles (static)
        - images
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
