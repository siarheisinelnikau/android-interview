# Default and named arguments, `vararg`, and the spread operator - how do they affect a function's call sites?

[Back to questions](../../README.md#kotlin)

**Level:** Junior · **Topic:** Kotlin

## Answer

Default values let callers omit optional arguments; named arguments make call sites readable and allow supported reordering. A `vararg` parameter accepts a variable number of values, represented as an array inside the function. The spread operator passes an existing array into a vararg position.

```kotlin
fun labels(prefix: String = "", vararg values: String) =
    values.map { prefix + it }
val input = arrayOf("a", "b")
val result = labels("#", *input)
```

Consider allocation and copying in hot paths rather than assuming varargs are free. Java interoperability has different call-site rules, and default arguments do not automatically generate every convenient Java overload. Parameter names also become important to Kotlin source callers using named arguments.

## References

- [Kotlin: functions and parameters](https://kotlinlang.org/docs/functions.html)
