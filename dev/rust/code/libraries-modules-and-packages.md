# Libraries, Modules & Packages

## Modules

```
src
    main.rs
    constant
        mod.rs
        server.rs
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
