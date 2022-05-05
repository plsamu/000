# SSG

## Examples

```tsx
import React, { useEffect, useState } from "react";
import { Button } from "../components/Button";

export const getStaticProps = async () => {
  const res = await fetch("https://jsonplaceholder.typicode.com/users")
  const posts = await res.json();
  return {
    props: {
      words: ["ciao", "makako", "giuggiola"],
      posts,
    },
  };
};

const Index = (props) => (
  <>
    <Button />
    {props.words}
    {props.posts.map((item, i) => {
      console.log(item);
      return <p key={i}>{item["name"]}</p>
    })}
  </>
);

export default Index;

```

