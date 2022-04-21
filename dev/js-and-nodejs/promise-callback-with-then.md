# Promise - Callback with "then"

## Simple Promise

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

## Async Promise

```javascript
jaasync function get_dark_color() {
  return new Promise((resolve, reject) => {
    let minimum = 130;

    let r = Math.floor(Math.random() * 255);
    while (r > minimum) r = Math.floor(Math.random() * 255);

    let g = Math.floor(Math.random() * 255);
    while (g > minimum) g = Math.floor(Math.random() * 255);

    let b = Math.floor(Math.random() * 255);
    while (b > minimum) b = Math.floor(Math.random() * 255);

    let a = Math.random();
    while (a < 0.45) a = Math.random().toFixed(2);

    console.log(r, g, b, a);
    // rgba(20,60,200,0.67423)
    resolve("rgba(" + [r, g, b, a].join(",") + ")");
  });
}
```
