# 000 - autorestart, logs

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

### Linux - systemd

example:

{% content-ref url="../../../linux/systemd/create-git-lan-server-service.md" %}
[create-git-lan-server-service.md](../../../linux/systemd/create-git-lan-server-service.md)
{% endcontent-ref %}

## Disable/Enable Logs

### From .env

{% embed url="https://github.com/actix/examples/tree/master/basics/todo" %}

```
[dependencies]
dotenv = "0.15.0"
```

```
/project
    src
        main.rs
    Cargo.toml
    .env
```

```
# .env
ENV1=world!
```

```rust
use std::{env};
use dotenv::dotenv;

fn main() {
    dotenv().ok();
    let daje = env::var("ENV1").ok().unwrap();
    println!("Hello, {}", daje);
}
```

### Also

{% content-ref url="../../../dev/003-languages/rust/code/log.md" %}
[log.md](../../../dev/003-languages/rust/code/log.md)
{% endcontent-ref %}
