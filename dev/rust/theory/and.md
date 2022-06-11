# &

## 000

```rust
impl Foo {

    // this method is asking for the ownership of a Foo instance
    // when this method finish, the instance is deleted from memory
    fn consume_self(self) {
        println!("eating");
    }

    // this method is only asking for the reference but
    // the ownership remains to who call this method
    fn use_self(&self) {
        println!("else");
    }
    
    // it's equals to use_self method above, just don't use this.
    fn use_self_with_boilerplate(self) -> Foo {
        println!("else");
        self
    }

}
```
