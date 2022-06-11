# Log

## Log Levels

* **TRACE**
* **DEBUG**
* **INFO**
* **WARN**
* **ERROR**
* **FATAL**

### Example

```
[dependencies]
log = { version = "0.4.0", features = ["max_level_trace", "release_max_level_warn"] }
```

**`max_level_trace`**

Will log, **in debug mode**, everything: trace, debug, info, warn, error, fatal.

**`release_max_level_warn`**

Will log, **in release mode:** warn, error, fatal

## env\_logger

*   you <mark style="color:red;">**`must`**</mark>set RUST\_LOG

    `e.g.`&#x20;

    `set RUST_LOG=trace`

```
C:\Windows\System32\cmd.exe /c "set RUST_LOG=info && start C:\Users\path\to\program.exe"
```

```rust
#[macro_use] extern crate nickel;
use log::{info, warn};
use nickel::Nickel;

fn main() {

    // just this
    env_logger::init();
    
    
    info!("Server Starting!");
    warn!("daje");

    let mut server = Nickel::new();

    server.utilize(router! {
        get "**" => |_req, _res| { "Hello world!"}
    });

    server.listen("127.0.0.1:6767").unwrap();
}
```

## Simplelog

```rust
use log::{info, warn};
use simplelog::{ColorChoice, Config, LevelFilter, TermLogger, TerminalMode};

fn main() {
    TermLogger::init(
        LevelFilter::Info,
        Config::default(),
        TerminalMode::Mixed,
        ColorChoice::Always,
    )
    .unwrap();
    info!("starting up");
    warn!("oops, nothing done");
}
```

## Sources

{% embed url="https://www.youtube.com/watch?v=7wQfqNiY-mY" %}
