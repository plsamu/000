# Theme Changer without JS

### isDark

```
http://192.168.1.100:3000/?dark   // is dark
http://192.168.1.100:3000/        // is not dark

http://192.168.1.100:3000/cv?dark        // is dark
http://192.168.1.100:3000/blog?dark      // is dark
```

### CSS

#### globals-constants.css

```css
@import url("https://fonts.googleapis.com/css2?family=Arvo:wght@400;700&display=swap");

html,
body {
  margin: auto;
  font-family: "Arvo";
  padding: 0;
  margin: 0;
}

* {
  box-sizing: border-box;
}
```

#### globals-dark.css

```css
html {
  background: rgb(27, 27, 27);
}

html,
body {
  color: aliceblue;
}
```

#### globals-light.css

```css
html {
  background: rgba(255, 187, 99, 0.747);
}

html,
body {
  color: rgb(0, 52, 97);
}
```

### project tree

```
api
public
    globals-constants.css
    globals-light.css
    globals-dark.css
src
    pages
        _app.tsx
        index.tsx
    containers
        withTheme
    components        // Atomic Design Methodology
        atoms
        molecules
            navbar
        organisms
        templates
```

### index.tsx

```tsx
function isDark(req) {
    return req.url.indexOf("?dark") > -1
}

export async function getServerSideProps({ req }) {
  return {
    props: {
      isDark: isDark(req),
    },
  };
}

class Home extends Component {
  render() {
    console.log(this.props);
    return (
      <>
        {this.props["isDark"] === true ? <p>is dark</p> : <p>is not dark</p>}
      </>
    );
  }
}

export default withTheme(Home);
```

### withTheme

```tsx
const withTheme = (Component) => {
  const wrappedComponent = (props) => {
    return (
      <>
        <Head>
        <link rel="stylesheet" href="/globals-constants.css" />
          {props["isDark"] === true ? (
            <link rel="stylesheet" href="/globals-dark.css" />
          ) : (
            <link rel="stylesheet" href="/globals-light.css" />
          )}
        </Head>
        <Navbar isDark={props["isDark"]}/>
        <Component {...props} />
      </>
    );
  };

  return wrappedComponent;
};

export default withTheme;
```

### navbar

```tsx
const Navbar = ({ isDark }) => {
  
  let setDark = ''
  isDark === true ? setDark='?dark' : ''

  return (
    <nav className="navbar">
      <a href={`/${setDark}`} className="navbarImg">
        <img src="./favicon.ico" />
      </a>
      <a href={`/blog${setDark}`} className="navbarItem">
        Blog
      </a>
      <a href={`/cv${setDark}`} className="navbarItem">
        CV
      </a>
      <a href={`/woi${setDark}`} className="navbarItem">
        Wall Of Internet
      </a>
    </nav>
  );
};

export default Navbar;
```
