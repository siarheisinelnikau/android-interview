# What does multi-dollar string interpolation solve when embedding JSON, templates, or source code containing `$` characters?

[Back to questions](../../README.md#kotlin-versions)

**Level:** Middle · **Topic:** Kotlin Versions · **Version:** Kotlin 2.1-2.2 · **Reviewed:** 2026-10-29

## Answer

Multi-dollar interpolation lets a string choose how many consecutive dollar signs start interpolation. This reduces escaping when the embedded content itself contains dollar-prefixed identifiers, such as JSON schema keys or generated source code. It became stable in Kotlin 2.2 after its preview in 2.1.

```kotlin
val name = "profile"
val json = $$"""{"$schema":"example","name":"$$name"}"""
```

Here a single dollar sign remains literal, while two introduce Kotlin interpolation. The prefix sets the rule for that string; it does not alter JSON escaping or validate the generated document.

For real structured payloads, prefer a serializer when possible. This feature improves string syntax but does not make manually concatenated SQL, HTML, or JSON safe for untrusted input.

## References

- [Kotlin: string interpolation](https://kotlinlang.org/docs/strings.html)
- [Kotlin 2.2: multi-dollar interpolation](https://kotlinlang.org/docs/whatsnew22.html)
