---
minutes: 30
---

# Exercise: Expression Evaluation

Let's write a simple recursive evaluator for arithmetic expressions. Start with
an enum defining the binary operations:

```rust
{{#include exercise.rs:Operation}}

{{#include exercise.rs:Expression}}

{{#include exercise.rs:Res}}

{{#include exercise.rs:eval}}
    todo!()
}

{{#include exercise.rs:tests}}
```

The `Box` type here is a smart pointer, and will be covered in detail later in
the course. An expression can be "boxed" with `Box::new` as seen in the tests.
To evaluate a boxed expression, use the deref operator to "unbox" it:
`eval(*boxed_expr)`.

Some expressions cannot be evaluated and will return an error. The `Res`
type represents either a successful value or an error with a message. This is
very similar to the standard-library `Result` which we will see later.

Copy and paste the code into the Rust playground, and begin implementing
`eval`. The final product should pass the tests. It may be helpful to use
`todo!()` and get the tests to pass one-by-one. You can also skip a test
temporarily with
`#[ignore]`:

```none
#[test]
#[ignore]
fn test_value() { .. }
```

If you finish early, try writing a test that results in an integer overflow.
How could you handle this with `Res::Err` instead of a panic?
