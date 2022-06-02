# 000 - Minimal

### add dependencies

```
[package]
name = "home_backend_events"
version = "0.1.0"
edition = "2021"

# See more keys and their definitions at https://doc.rust-lang.org/cargo/reference/manifest.html

[dependencies]
nickel = "*"      <----------- NEW
```

{% embed url="https://nickel-org.github.io/" %}

### main.rs

```rust
#[macro_use] extern crate nickel;

use nickel::Nickel;

fn main() {
    let mut server = Nickel::new();

    server.utilize(router! {
        get "**" => |_req, _res| { "Hello world!"}
    });

    server.listen("127.0.0.1:6767").unwrap();
}
```

## run

```
cargo run
```

{% embed url="http://127.0.0.1:6767" %}

{% hint style="info" %}
THE FUCK =O
{% endhint %}
