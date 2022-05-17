# Menu on the left, content on the right

```css
:root {
  --my-navbar-width: 200px;
}

.content{
  width: 100%;
  margin-left: var(--my-navbar-widht);
  height: 100%;
  border: 1px solid black;
}

.navbar {
  position: absolute;
  top: 0;
  left: 0;
  display: flex;
  flex-direction: column;
  width: var(--my-navbar-widht);
  height: 100%;
  padding: 10px;
}
```
