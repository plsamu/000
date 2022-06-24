# 001 - actix

## List of examples

* [basic with static files](https://github.com/actix/examples/tree/master/basics/basics)
* [postgres connection](https://github.com/actix/examples/tree/master/databases/postgres)
* [some auth examples](https://github.com/actix/examples/tree/master/auth)

## Structure

### static

```
/server_project
    src
        mstatic
            mod.rs
        main.rs
    Cargo.toml
    static
        favicon.png
```

## main.rs

```rust
pub fn configure(cfg: &mut ServiceConfig) {
    /* cfg.data(API::new(addr))
        .route("/info", web::get().to(API::info))
        .route("/log", web::get().to(API::log))
        .route("/probe", web::post().to(API::probe))
        .route(
            "/update/download/abort",
            web::post().to(API::download_abort),
        ); */
}

#[actix_rt::main]
async fn main() -> std::io::Result<()> {
    HttpServer::new(|| {
        App::new().configure(configure)
    })
    .bind("127.0.0.1:8080")?
    .run()
    .await
}
```
