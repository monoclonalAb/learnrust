## structs

```rust
struct Gift{
    is_expensive: bool,
    price: i32,
    type: String,
}

fn main() {
    let my_gift = Gift{
        is_expensive: true,
        price: 1000,
        type: String::from("Macbook"),
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
    // myGift.type => gone, since moved into myGift2
}
```

