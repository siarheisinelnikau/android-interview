# What do data classes generate? Why is `copy()` a shallow copy, and which properties participate in equality?

[Back to questions](../../README.md#kotlin)

**Level:** Middle · **Topic:** Kotlin

## Answer

A data class normally generates `equals`, `hashCode`, `toString`, `componentN` functions, and `copy` using properties declared in the primary constructor. Properties declared only in the class body do not automatically participate in that generated equality or copying contract.

`copy()` is shallow: it copies references to nested objects rather than recursively cloning them.

```kotlin
data class Basket(val items: MutableList<String>)
val first = Basket(mutableListOf("book"))
val second = first.copy()
second.items.add("pen") // first.items sees the same mutation.
```

Prefer immutable nested values for snapshot-like models. Destructuring calls component functions in order; it does not inspect property names. A data class reduces boilerplate but does not guarantee immutability, domain validity, or correct identity semantics for every use case.

## References

- [Kotlin: data classes](https://kotlinlang.org/docs/data-classes.html)
