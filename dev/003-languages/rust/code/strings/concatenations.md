# Concatenations

{% embed url="https://stackoverflow.com/questions/30154541/how-do-i-concatenate-strings" %}

## Concat and consume

```rust
use rpassword::read_password;
use std::{io::Write};

/**
 * parameters are consumed (because are owned by this fn)
 * returns an owned String
 */
fn concat_and_consume(str1: String, str2: String) -> String {
    str1 + &str2
}

pub fn init() {
    print!("Type password: ");
    std::io::stdout().flush().unwrap();
    let password = read_password().unwrap();
    let placeholder = "host=127.0.0.1 user=postgres port=6543 dbname=postgres password=".to_owned();
    let conn_string = concat_and_consume(placeholder, password);
    println!("{}", conn_string);
}

```
