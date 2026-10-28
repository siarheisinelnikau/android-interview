# Compare `lateinit` and delegated properties such as `by lazy`. What thread-safety options does `lazy` provide?

[Back to questions](../../README.md#kotlin)

**Level:** Middle · **Topic:** Kotlin

## Answer

`lateinit` defers initialization of an eligible non-null var. Reading it before initialization throws, and it does not automatically provide thread synchronization. It is useful when a framework or lifecycle initializes a property after construction, though constructor initialization is easier to reason about when available.

`by lazy` is a delegated val initialized on first access. On the JVM, the default synchronized mode ensures one published initialization. PUBLICATION can run the initializer more than once but publishes one result; NONE provides no thread-safety guarantees.

Choose based on who initializes the value and when access begins. An expensive lazy initializer can still block the main thread on its first read. Neither mechanism releases a resource or prevents retaining an obsolete Activity.

## References

- [Kotlin: delegated properties and lazy](https://kotlinlang.org/docs/delegated-properties.html)
- [Kotlin: late-initialized properties](https://kotlinlang.org/docs/properties.html)
