## structs

```rust
struct Gift{
    is_expensive: bool,
    price: i32,
    kind: String,
}

fn main() {
    let my_gift = Gift{
        is_expensive: true,
        price: 1000,
        kind: String::from("Macbook"),
    }
}
```

- if we want to edit certain fields, the entire `struct` *must be mutable*
```rust
fn main() {
    let mut my_gift = Gift {
        // ...
    }
}
```

- can also init using certain fields from other instances:
```rust
fn main() {
    // include previous gift

    let my_gift_2 = Gift {
        is_expensive: false,
        ..my_gift
    }

    // myGift.isExpensive => wasn't taken; still exists
    // myGift.price => copy field; still exists
    // myGift.kind => gone, since moved into myGift2
}
```

## debug printing

```rust
#[derive(Debug)]                        // opts into "debug" trait
struct rectangle {
    width: u32,
    height, u32,
}

fn main() {
    let rect1 = Rectangle {
        width: 30,
        height: 50,
    }

    println!("rect1 is {rect1:?}")      // specifier ":?" tells us `println!` to use the `Debug` output format
                                        // output: "rect1 is Rectangle { width: 30, height: 50 }"
                                        
                                        // specifier ":#?" adds lines
                                        // output:
                                        // "rect1 is Rectangle {
                                        //      width: 30
                                        //      width: 50
                                        // }"
}
```

- NOTE: also exists `dbg!` macro => takes ownership, macro, then returns it
    - unlike `println!` which passes a reference

## methods:

- u write methods separately to `struct`

```rust
struct Gift{
    is_expensive: bool,
    price: i32,
    count: i32,
    kind: String,
}

impl Gift {
    fn total_price(&self) -> i32 {
        self.price * self.count
    }
}

let new_gift = Gift { 
    // ...
}

new_gift.total_price();
```

### associated functions

- associated functions are functions defined for a specific type
    - only difference is the first definition is **not `self`**

```rust
// struct definition

impl Gift {
    fn new() -> Self {
        Self {
            isExpensive: false,
            price: 0,
            count: 0,
            kind: String::from("Unknown"),
        }
    }
}

let new_gift = Gift::new();
```
