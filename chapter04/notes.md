## ownership:

- each value in rust has *one* owner (only one at a time)
    - when owner gets out of scope, the value will be dropped

- for memory on the heap, the memory gets returned back to the memory allocator *at the end of the scope*
    - (instead of having to *free* the memory yourself)
```rust
fn main(){
    let s = String::from("hello")
    
}   // s is no longer valid here
    // 'drop' function is called automatically to return `s` back to memory
```

- heap-only copy => moving
    - same thing would occur if i tried to reassign `s2`
    - NOTE: stack-only copy with certain types => copying (e.g. with `int`, `float`, `bool`, `char` etc.)
```rust
fn main(){
    let s1 = String::from("hello");
    let s2 = s1;                // counts as a *move*; `s1` is no longer valid

    println!("{s1}, world!");   // therefore, returns an error
}
```
- similar thing would happen w/ functions:
    - 
    - return values also transfers ownership of values (back to the caller)
    - issue is, what if we want to keep ownership but not have to return? **references**
```rust
fn main(){
    let s = String::from("hello");

    takes_ownership(s);         // s's value moves into this function...
                                // ...s is not valid here!
}
```

## references:

```rust
let s1 = String::from("hello!");

let len = calculate_length(&s1);    // uses a reference to the object INSTEAD of transfering ownership
```
- allows us to "borrow" the value
    - NOTE: we can't mutate the value (since we are borrowing and only have a reference to the object)
- but we can do that with a *mutatable reference*

```rust
fn main() {
    let mut s = String::from("hello");  // add `mut` onto the type

    change(&mut s);                     // add `mut` onto the reference
}

fn change(some_string: &mut String) {   // add `mut` onto the argument
    some_string.push_str(", world");
}
```


