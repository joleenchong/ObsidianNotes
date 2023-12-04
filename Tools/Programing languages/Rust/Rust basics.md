Creating new projects
```bash
# Creates new cargo folder
cargo new file_name
cd file_name
# Building rust program
cargo build
# Running rust program
cargo run
# Checks for compilation errrors, but no executable created - faster
cargo check
# Compile for release
cargo build --release
```

Rust hello world:
```rust
fn main() {
	println!("Hello World!");
}
```
- `println!` is a macro, so it uses a ! before the parentheses. Functions would not have a !

Assigning variables:
```Rust
let variable =  5; //creates an immutable variable with value 5
let mut variable = String::new(); //creates mutable variable
//String::new() makes new instance of String. :: says that new() is a function of String
```

User input:
```Rust
use std::io; //standard io library needed

io::stdin().read_line(&mut variable);
//& is a reference
//References are immutable by default. That's why you can't use &variable.
```

Error handling:
```Rust
.expect("Failed to read line");
//Some methods return Result values, which can be Ok and Err
//On Result being an Err state, print "Failed to read line"
```


