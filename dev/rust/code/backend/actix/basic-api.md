# Basic API

### Basic

```rust
#[actix_rt::main]
async fn main() -> std::io::Result<()> {
    HttpServer::new(|| App::new().configure(configure))
        .bind((constant::server::IP, constant::server::PORT))?
        .run()
        .await
}
```

### Method 0 - handler - not working

```rust
use actix_web::{App, HttpResponse, HttpServer, web::{Bytes, post}};

fn handler(bytes: Bytes) -> Result<String, HttpResponse> {
    match String::from_utf8(bytes.to_vec()) {
        Ok(text) => Ok(format!("Hello, {}!\n", text)),
        Err(_) => Err(HttpResponse::BadRequest().into())
    }
}

fn main() {
    HttpServer::new(||{
        App::new().route("/name", post().to(handler))
    }).bind("127.0.0.1:8080")
        .unwrap()
        .run()
        .unwrap();
}
```

### Method 1

```rust
#[get("/api/test")]
async fn api_get_example(req: HttpRequest) -> Result<HttpResponse, Error> {
    Ok(HttpResponse::build(StatusCode::OK)
        .content_type(ContentType::plaintext())
        .body("api_get_example"))
}

pub fn configure(cfg: &mut ServiceConfig) {
    cfg.service(api_get_example)
}
```

### Method 2

```rust
async fn getIndex() -> HttpResponse {
    HttpResponse::Ok().body("index opened")
}

pub fn configure(cfg: &mut ServiceConfig) {
    cfg.service(web::resource("/").route(web::get().to(getIndex)))
}
```
