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

#### Setup dependencies flags (I like this)

{% embed url="https://docs.rs/log/latest/log/index.html#compile-time-filters" %}

This is an example on how Crate Log can disable logs in debug:

* until info level logs (`max_level_info`)

In release:

* trace, debug, and info are disabled (`release_max_level_warn`)

With the following configuration:

```
[dependencies]
log = { version = "0.4.0", features = ["max_level_info", "release_max_level_warn"] }
```

{% hint style="warning" %}
Crate Log needs an implementation!
{% endhint %}

## env\_logger implementation

env\_logger is a simple implementation of "crate log" module.

{% hint style="warning" %}
you need to setup the RUST\_LOG env var
{% endhint %}

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
    info("Starting Server!");
    debug("FOOOOOOOOOOOOK");

    let mut server = Nickel::new();

    server.utilize(router! {
        get "**" => |_req, _res| { "Hello world!"}
    });

    server.listen("127.0.0.1:6767").unwrap();
}
```

## Disable LOGs using env\_logger

{% hint style="danger" %}
When you build the executable, thing are different...
{% endhint %}

### In debug / development&#x20;

```batch
set RUST_LOG=debug && cargo run
```

### In release

TBD







