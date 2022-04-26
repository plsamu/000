# Blog + Tor - JS

## TODO

```
[ ] server side rendering
[ ] use of gzipping and caching
[ ] detect if javascript or non-javascript user
[ ] detect if from clearnet or from tor
```

## 1. Tor

{% content-ref url="../../ict/hidden-services-aka-onion-services/setup-an-hidden-service.md" %}
[setup-an-hidden-service.md](../../ict/hidden-services-aka-onion-services/setup-an-hidden-service.md)
{% endcontent-ref %}

## 2. System Meditations

I want to use NodeJS for backend and serve only html+css pages.\
Idk anything about gzipping and caching.\
Idk what are the good practices to render pages server side.

<details>

<summary>Some sources</summary>

[https://medium.com/@baphemot/whats-server-side-rendering-and-do-i-need-it-cb42dc059b38](https://medium.com/@baphemot/whats-server-side-rendering-and-do-i-need-it-cb42dc059b38)

[https://www.digitalocean.com/community/tutorials/react-server-side-rendering](https://www.digitalocean.com/community/tutorials/react-server-side-rendering)

[https://nextjs.org/docs/basic-features/pages#two-forms-of-pre-rendering](https://nextjs.org/docs/basic-features/pages#two-forms-of-pre-rendering)

[https://www.reddit.com/r/TOR/comments/hllf94/server\_side\_rendering\_and\_noscript/](https://www.reddit.com/r/TOR/comments/hllf94/server\_side\_rendering\_and\_noscript/)

</details>

<details>

<summary>NextJS tutorial</summary>

[https://www.youtube.com/watch?v=A63UxsQsEbU\&list=PL4cUxeGkcC9g9gP2onazU5-2M-AzA8eBw](https://www.youtube.com/watch?v=A63UxsQsEbU\&list=PL4cUxeGkcC9g9gP2onazU5-2M-AzA8eBw)

</details>

### Server side html rendering (SSR) vs Static Site Generation (SSG)

These are two pre-rendering techniques.

> Imagine that we are creating a simple blog website. The content will be totally statically-generated, right? We will have only a few pages and the content will be fetched from our server, so it makes total sense to go with SSG in this case.

## 3. NextJS without client side JS

{% hint style="warning" %}
To prevent to create client side JS with NextJS, it necessary to avoid using some NextJS object like \<Link>\</Link>
{% endhint %}
