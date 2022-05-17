# Build / Prebuild

{% embed url="https://github.com/vercel/next.js/discussions/17479#discussioncomment-1438251" %}

```
package.json
scripts
    load-gitbook
```

```
  "scripts": {
    "prebuild": "./scripts/load-gitbook",
    "build": "next build",
    ...
  }
```

