# What do context parameters solve compared with extension receivers and explicit parameters? How do they differ from the older context receivers feature?

[Back to questions](../../README.md#kotlin)

**Level:** Senior · **Topic:** Kotlin

## Answer

Context parameters declare dependencies resolved from matching values available at the call site, without making each dependency an extension receiver. Named parameters make their use inside the function explicit.

```kotlin
context(logger: Logger)
fun recordOpened(id: Long) {
    logger.log("Opened $id")
}
```

An extension receiver primarily adds receiver-style callable syntax to one type. Ordinary explicit parameters keep every argument visible in each call. Context parameters can reduce repetitive passing for consistently available capabilities, but they introduce contextual resolution and possible ambiguity.

They replace the older experimental context receivers design rather than merely renaming its syntax. Use them when the surrounding dependency context is clear, and check the exact Kotlin release and the status of related capabilities such as explicit context arguments.

## References

- [Kotlin: context parameters](https://kotlinlang.org/docs/context-parameters.html)
