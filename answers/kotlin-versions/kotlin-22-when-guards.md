# How do guard conditions in `when` simplify branching? What changed between their preview in 2.1 and stabilization in 2.2?

[Back to questions](../../README.md#kotlin-versions)

**Level:** Middle · **Topic:** Kotlin Versions · **Version:** Kotlin 2.1-2.2 · **Reviewed:** 2026-10-29

## Answer

A guard adds an additional condition to a `when` branch after its primary match, such as a type check. The branch runs only when both the primary match and guard succeed, and the successful primary check can provide useful smart casts inside the guard.

```kotlin
when (result) {
    is Download.Ready if result.bytes > 0 -> display(result)
    is Download.Ready -> showEmpty()
    is Download.Failed -> showError(result)
}
```

Guard conditions were introduced in preview in Kotlin 2.1 and stabilized in 2.2. A guarded case does not necessarily cover every value of its type, so include the remaining case when exhaustiveness requires it. Keep guards clear and avoid making branch selection depend on hidden expensive side effects.

## References

- [Kotlin 2.2: stable guard conditions](https://kotlinlang.org/docs/whatsnew22.html)
- [Kotlin: when guards](https://kotlinlang.org/docs/control-flow.html)
