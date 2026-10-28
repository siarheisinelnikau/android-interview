# When can non-local `break` and `continue` be used inside inline lambdas? How do they differ from returning from a lambda?

[Back to questions](../../README.md#kotlin-versions)

**Level:** Middle · **Topic:** Kotlin Versions · **Version:** Kotlin 2.1-2.2 · **Reviewed:** 2026-10-28

## Answer

Kotlin 2.2 stabilized non-local break and continue in eligible inline lambdas. They can target an enclosing loop at the call site rather than merely ending the current lambda.

```kotlin
for (number in numbers) {
    run {
        if (number < 0) continue
    }
    process(number)
}
```

By contrast, a labeled return such as `return@forEach` returns from that lambda invocation; it is not a general spelling of continue for an outer loop. Non-local control flow requires an eligible inline context and cannot be assumed to work from stored, asynchronous, noinline, or crossinline callbacks.

Prefer straightforward loop structure when it is clearer. The feature can remove awkward workarounds, but deeply nested non-local exits can make control flow difficult to follow.

## References

- [Kotlin 2.2: non-local break and continue](https://kotlinlang.org/docs/whatsnew22.html)
- [Kotlin: returns and jumps](https://kotlinlang.org/docs/returns.html)
