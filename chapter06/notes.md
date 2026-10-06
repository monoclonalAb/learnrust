## enums

```cpp
enum RunKind {
    ShortRun,
    LongRun,
}

let todays_run = RunKind::short_run;
```

```rust
// can add values inside:
enum RunKind {
    ShortRun(u32),
    LongRun(u32),
}

let todays_run = RunKind::long_run(21000);
```

```rust
enum Message{
    Quit,
    Move { x: i32, y: i32 },
    Write(String),
    ChangeColor(i32, i32, i32),
}

impl Message {
    fn call(&self) {
        // method body would be defined here
    }
}

let m = Message::Write(String::from("hello"));
m.call();
```

```rust
// enums that can encode a value being present / absent

enum Option<T> {
    None,
    Some(T),
}

let some_number = Some(5);
let some_word = Some(String::from("hello"));

let absent_number: Option<i32> = None;

// good for preventing mixing of types:
let another_number: i8 = 5;
let final_number: Option<i8> = 6;

// (final_number + another_number) would return an error since different types
```

## match    

```rust
enum Coin {
    Penny,
    Nickel,
    Dime,
    Quarter(UsState),
}

fn value_in_cents(coin: Coin) -> u8 {
    match coin {
        Coin::Penny => {
            println!("Lucky penny!");
            1
        },
        Coin::Nickel => 5,
        Coin::Dime => 10,
        Coin::Quarter(state) => {
            println!("State quarter from {state:?}!");
            25
        }
    }
}

// can match with Option<T>

// last value acts as a "catch-all"
let dice_roll = 9;
match dice_roll {
    3 => add_fancy_hat(),
    7 => remove_fancy_hat(),
    other => move_player(other),
}

// or

match dice_roll {
    3 => add_fancy_hat(),
    7 => remove_fancy_hat(),
    _ => reroll(),
}
```
