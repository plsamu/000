# Node & NPM

### check versions

```bash
node_v=$(node -v)

if [ "$node_v" != "v16.14.2" ]; then
    echo "bla bla"
    exit 1
fi
```
