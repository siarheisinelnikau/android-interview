# Compare `Unit`, `Nothing`, and nullable return types. When is each useful?

[Back to questions](../../README.md#kotlin)

**Level:** Middle · **Topic:** Kotlin

## Answer

`Unit` is a real type with one value and normally communicates that a function has no meaningful result. `Nothing` has no values and describes an expression that never completes normally, such as a function that always throws. A nullable return type communicates a possible missing result.

```kotlin
fun report(message: String): Unit = println(message)
fun fail(message: String): Nothing = error(message)
fun lookup(id: Long): User? = users[id]
```

Nothing is a subtype of other types, allowing throw/return expressions to fit branches whose normal result has another type. Null is not Unit, and returning null is not equivalent to never returning. Choose a result model that makes absence, failure, and successful completion distinct when the domain needs that distinction.

## References

- [Kotlin: Unit and Nothing](https://kotlinlang.org/docs/returns.html)
