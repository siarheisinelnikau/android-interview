# Compare `let`, `run`, `with`, `apply`, and `also`. What are the risks of nesting scope functions?

[Back to questions](../../README.md#kotlin)

**Level:** Middle · **Topic:** Kotlin

## Answer

Scope functions differ mainly in the receiver name and returned value. `let` and `also` expose `it`; `run`, `with`, and `apply` use a receiver as `this`. `let`, `run`, and `with` return the block result, while `apply` and `also` return the original object.

Use `apply` for configuring an object, `also` for a side action while preserving it, and `let` or `run` for a scoped transformation. `with` is a regular function taking the receiver as an argument.

These are convenience functions, not lifecycle, synchronization, or transaction primitives. Deep nesting makes it unclear which `this` or `it` is used and can hide return behavior. A named local variable is often clearer than choosing another scope function to make a chain shorter.

## References

- [Kotlin: scope functions](https://kotlinlang.org/docs/scope-functions.html)
