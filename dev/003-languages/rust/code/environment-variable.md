# Environment variable

## Load env

### PowerShell

```batch
 $Env:CASE_INSENSITIVE=1; cargo run to poem.txt
 Remove-Item Env:CASE_INSENSITIVE
```

## Load env from file

{% embed url="https://crates.io/crates/dotenv" %}

{% hint style="info" %}
[dotenv](https://docs.rs/dotenv/latest/dotenv/fn.dotenv.html)

This is usually what you want. It loads the .env file located in the environment's current directory or its parents in sequence.
{% endhint %}

### filetree

```
src
    main.rs
.env
```

### .toml

```
dotenv = "^0.15.0"
```

### .env

```
ENV1="test one"
```

### code

```rust
use std::env;
use dotenv;

fn main() {
    dotenv::dotenv().ok();
    match env::var("ENV1") {
        Ok(value) => println!("{}: {}", "ENV1", value),
        Err(e) => panic!("${} is not set ({})", "ENV1", e)
    }
}
```
