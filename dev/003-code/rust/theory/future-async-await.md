# Future, async / await

{% embed url="https://www.youtube.com/watch?v=NNwK5ZPAJCk" %}

{% embed url="https://stackoverflow.com/questions/61292425/how-to-run-an-asynchronous-task-from-a-non-main-thread-in-tokio" %}

{% embed url="https://www.youtube.com/watch?v=2WXNY1ppTzY" %}

```rust
// db
let rt_m = tokio::runtime::Builder::new_multi_thread().build().unwrap();
rt_m.spawn(async move {
    mdb::db::tokio_db();
});
```
