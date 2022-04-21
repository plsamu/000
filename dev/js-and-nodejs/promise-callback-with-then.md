# Promise - Callback with "then"

```
innocent-face:ʘ‿ʘ
table-flip:(╯°□°）╯︵ ┻━┻
tidy-up:┬─┬⃰͡ (ᵔᵕᵔ͜ )
fisticuffs:ლ(｀ー´ლ)
surprised:（　ﾟДﾟ）
shrug-face:¯\_(ツ)_/¯
```

```javascript
const get_random_emoji = new Promise((resolve, reject) => {
  const url = "/res/ascii-emojis";
  fetch(url)
    .then((r) => r.text())
    .then((t) => {
      const allLines = t.split(/\r\n|\n/);
      const randomElement = Math.floor(Math.random() * allLines.length);
      let line = allLines[randomElement];
      resolve(line.split(/:/)[1]);
    });
});

window.onload = () => {
  get_random_emoji.then((emoji) => {
    document.title = emoji;
  });
};
```
