# Experimental collection literals - how does the expected type affect `[]`, and when is a custom `operator fun of` needed?

[Back to questions](../../README.md#kotlin-versions)

**Level:** Middle · **Topic:** Kotlin Versions · **Version:** Kotlin 2.4 · **Reviewed:** 2026-10-29

## Answer

Kotlin 2.4 introduces experimental collection literals using bracket syntax. The expected type participates in selecting what is constructed; when there is no more specific expected collection type, the documented default is List.

```kotlin
// Kotlin 2.4: requires the experimental -Xcollection-literals option.
val values: List<Int> = [1, 2, 3]
```

Custom supported types can provide a companion `operator fun of` construction function. This is different from simply indexing an existing object with `get`. The initial implementation also has limitations, including Java-defined collection construction, so check the exact compiler support and opt-in configuration.

Bracket syntax does not promise deep immutability or a particular performance improvement. Keep published examples explicit about their experimental requirement so readers do not mistake a stable compiler release for universally enabled syntax.

## References

- [Kotlin 2.4: experimental collection literals](https://kotlinlang.org/docs/whatsnew24.html)
