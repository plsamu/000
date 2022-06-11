# Associated

{% hint style="info" %}
Called directly from the struct type
{% endhint %}

* items (trait)
* functions
* type

### function

```rust
struct Server {
    addr: String,
}

impl Server {
    fn new(addr: string) -> Server {
        Server {
            addr
        }
    }
}

Server::new("127.0.0.1:8080");
```
