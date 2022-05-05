# General

## Common Project Tree

```
src
    components
    pages
    styles (dynamic, likely use JS)
public
    imges
    styles (static, without JS)

```

## SSR, SSG, CSR

### SSR - Server Side Rendering

* [getServerSideProps](https://nextjs.org/docs/basic-features/data-fetching/get-server-side-props)

### SSG - Static Site Generation

Content is generated once, at build time.

* [getStaticProps](https://nextjs.org/docs/basic-features/data-fetching/get-static-props)
* [Incremental Static Regeneration](https://nextjs.org/docs/basic-features/data-fetching/incremental-static-regeneration) (update static pages _after_ you’ve built your site)

### CSR - Client Side Rendering

* useEffect (classic)

## VSCode shortcut

```
/* 
    File -> Preferences -> Keybindings
    ctrl ù              line comment
    maiusc alt a        block comment
    maiusc alt f        format page
*/
```
