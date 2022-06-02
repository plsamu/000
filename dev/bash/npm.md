# NPM

### delete all NPM modules from all folder recursivly

```
find . -name 'node_modules' -type d -prune -exec rm -rf '{}' +
```
