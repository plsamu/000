# Binary, Libraries, Modules & Packages

## Binary

{% hint style="warning" %}
if it has a `main.rs` (entry point) it's a binary
{% endhint %}

## Binary with module

```
/project
    src
        main.rs
        constant
            mod.rs
            server.rs
    Cargo.toml
```

### main.rs

```rust
mod constant;
constant::server::IP;
```

### mod.rs

```
pub mod server;
```

### server.rs

```rust
pub const IP: &str = "127.0.0.1";
```

### Another way -  1

1. delete server.rs
2. modify mod.rs with:

```rust
pub mod server {
    pub const IP: &str = "127.0.0.1";
}
```

### Another way - 2

```
/project
    Cargo.toml
    src
        main.rs
        constant.rs
```

1. delete constant folder
2. create constant.rs and write:

```rust
pub mod server {
    pub const IP: &str = "127.0.0.1";
}ì
```

## Library

{% hint style="info" %}
has lib.rs inside
{% endhint %}

![](<../../../../../.gitbook/assets/image (1).png>)
