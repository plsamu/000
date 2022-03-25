# Utils

### delete all NPM modules from folder recursivly

```
find . -name 'node_modules' -type d -prune -exec rm -rf '{}' +
```
