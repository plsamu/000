# Custom Modules

## Example 1 - index files

```
myproject
.
├── index.js
├── backend
│    └── index.js
├── frontend
│    └── index.js
└── package.json
```

### ./index.js

```javascript
const backend = require('./backend')
backend.printMsg()
```

### ./backend/index.js

```javascript
exports.printMsg = function () {
  console.log("Node.js is awesome!");
};
```

