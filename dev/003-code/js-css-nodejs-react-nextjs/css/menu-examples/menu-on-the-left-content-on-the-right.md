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
  position: fixed;
  height: 100%;
  width: var(--my-navbar-widht);
  
  display: flex;
  flex-direction: column;
  padding: 10px;
}
```
