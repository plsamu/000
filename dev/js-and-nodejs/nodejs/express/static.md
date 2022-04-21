# static

### Mind the differences

```javascript
app.use("/", express.static(path.join(__dirname, "public")));
app.use(express.static(path.join(__dirname, "public")));
```
