# 001 - autorestart, log disable/enable

## Auto restart when crash

### Windows - batch

```batch
@echo off

::Start server
:Start 
C:\path\to\application.exe

:: Wait 1 second before restarting if crash
TIMEOUT /T 1
GOTO:Start
```

## Disable/Enable Logs

{% embed url="https://docs.rs/log/latest/log/index.html#available-logging-implementations" %}
Available logging implementations
{% endembed %}

### env\_logger

env\_logger is a simple implementation of "crate log" module.

```
[dependencies]
log = { version = "0.4.0" }
env_logger = "0.8.4"
```

### Code

```rust
#[macro_use] extern crate nickel;
use log::{info, debug};
// also this: #[macro_use] extern crate log;

use nickel::Nickel;

fn main() {
    env_logger::init();    // MUST
    info!("Starting Server!");
    debug!("FOOOOOOOOOOOOK");

    let mut server = Nickel::new();

    server.utilize(router! {
        get "**" => |_req, _res| { "Hello world!"}
    });

    server.listen("127.0.0.1:6767").unwrap();
}
```

{% hint style="info" %}
There are two ways to setup logs filter
{% endhint %}

### Setup env

```batch
set RUST_LOG=debug && cargo run
```

### Setup dependencies flags (I like this)

{% embed url="https://docs.rs/log/latest/log/index.html#compile-time-filters" %}
Filters
{% endembed %}

For example, a crate can disable everything until info level logs in debug builds and trace, debug, and info level logs in release builds with the following configuration:

```
[dependencies]
nickel = "*"
log = { version = "0.4.0", features = ["max_level_info", "release_max_level_warn"] }
env_logger = "0.8.4"
```

