# Explain common and platform source sets. When would you use `expect`/`actual` declarations vs. interfaces with injected implementations?

[Back to questions](../../README.md#kotlin-multiplatform-optional)

**Level:** Middle · **Topic:** Kotlin Multiplatform (Optional)

## Answer

A common source set can use APIs supported by all targets it compiles to. Platform source sets can access their platform APIs, and intermediate source sets can share code among a subset of targets through the supported hierarchy.

Use expect/actual when common code needs a platform-provided declaration with a matching implementation for each relevant target. Ordinary interfaces and injected implementations are often simpler when several implementations or test doubles are useful.

```kotlin
interface DeviceClock { fun nowMillis(): Long }
class ExpiryPolicy(private val clock: DeviceClock)
```

Construct the appropriate platform clock at the boundary instead of forcing every dependency through expect/actual. Avoid duplicating injection mechanisms without a reason, and check the current stability of advanced declaration forms such as expected classes separately from ordinary expected functions.

## References

- [Kotlin: source-set hierarchy](https://kotlinlang.org/docs/multiplatform/multiplatform-hierarchy.html)
- [Kotlin: expect and actual](https://kotlinlang.org/docs/multiplatform/multiplatform-expect-actual.html)
- [Kotlin: platform API design choices](https://kotlinlang.org/docs/multiplatform/multiplatform-connect-to-apis.html)
