---
title: "Ownership and Borrowing in Rust"
datePublished: Fri Mar 10 2023 13:01:39 GMT+0000 (Coordinated Universal Time)
cuid: clf2jradq016dhqnvdzxmdvos
slug: ownership-and-borrowing-in-rust
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1677307350783/f05a32ff-f91c-414c-b744-8365113f7fac.png
tags: rust, programming-languages, rust-lang, ownership, borrowing

---

Ownership and borrowing are fundamental concepts in Rust that help ensure memory safety and prevent common programming errors like data races and null pointer dereferences. In this blog, we'll explore what ownership and borrowing are, and how they work in Rust.

## Ownership in Rust

In Rust, ownership is a concept that ensures that every value has a unique owner, which is the variable that holds the value. The owner has the exclusive right to modify or destroy the value, and Rust enforces these rules at compile-time to prevent memory-related bugs like data races, null pointer dereferences, and memory leaks.

When a variable goes out of scope, Rust automatically deallocates the memory associated with that value. This means that when a function returns, or when a block of code ends, any values declared within that scope are automatically cleaned up by Rust. This feature ensures that memory is freed when it is no longer needed, preventing memory leaks and making Rust programs more efficient and reliable.

The ownership model in Rust also provides a guarantee of memory safety. Since there is only one owner for each value, it is impossible to have two or more pointers to the same value which could lead to undefined behaviour or data races. Additionally, Rust's borrow checker enforces strict rules around borrowing and mutation of values to ensure that multiple parts of a program can access the same value without introducing bugs.

Let's look at an example:

```rust
fn main() {
    let x = "hello";
    {
        let y = "world";
        println!("{} {}", x, y);
    }
    println!("{}", x);
}
```

In this code, the variables `x` and `y` are allocated on the stack when the program runs. When the inner block ends, Rust automatically deallocates the memory for the variable `y`. When the function `main()` ends, Rust deallocates the memory for the variable `x`. This ensures that the memory is properly managed and that there are no memory leaks.

The ownership model in Rust is enforced at compile-time, and the compiler checks that each value has a unique owner and that the memory is properly managed throughout the program's execution. This guarantees memory safety and helps prevent common memory-related bugs like null pointer dereferences, buffer overflows, and use-after-free errors.

## Borrowing in Rust

Ownership is a powerful concept, but sometimes we need to allow multiple parts of our program to access the same value. This is where "borrowing" comes in.

In Rust, we can borrow a value using a reference. A reference is a pointer to a value, but unlike a traditional pointer, references have strict lifetime rules that ensure they remain valid and do not outlive the data they point to.

Here's an example of borrowing in Rust:

```rust
fn main() {
    let s1 = String::from("hello");
    let len = calculate_length(&s1);
    println!("The length of '{}' is {}.", s1, len);
}

fn calculate_length(s: &String) -> usize {
    s.len()
}
```

In this example, we define a function `calculate_length` that takes a reference to a `String` value. The `&` symbol in the function signature indicates that `s` is a reference to a `String`, rather than an owned value. This means that ownership of `s1` is not transferred to `calculate_length`, but rather a temporary reference to `s1` is created and passed to the function.

The `calculate_length` function then returns the length of the string, which is printed to the console along with the original string \`s1\`.

## Conclusion

Ownership and borrowing are fundamental concepts in Rust that are essential for ensuring memory safety and avoiding common programming errors. By grasping these concepts, you can write Rust code that is safer and more reliable.

In Rust, every value has a unique owner, which means that the variable that holds the value has exclusive control over it. Ownership ensures that memory is properly managed, and it helps prevent issues like memory leaks, data races, and null pointer dereferences.

Borrowing is another key concept in Rust that enables you to pass references to values without transferring ownership. This allows multiple parts of a program to access the same value without creating additional copies or risking memory-related errors.

Overall, understanding ownership and borrowing in Rust is crucial for writing safe and efficient code that is free from common memory-related bugs.