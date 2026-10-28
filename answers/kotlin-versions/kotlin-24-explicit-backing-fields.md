# How do stable explicit backing fields let you expose `StateFlow` while keeping a `MutableStateFlow` field, without a second backing property?

[Back to questions](../../README.md#kotlin-versions)

**Level:** Middle · **Topic:** Kotlin Versions · **Version:** Kotlin 2.4 · **Reviewed:** 2026-10-29

## Answer

Explicit backing fields let a property's public type differ from its private storage type without a separately named backing property. The feature was experimental in 2.3 and became stable in 2.4.

```kotlin
class SessionState {
    val active: StateFlow<Boolean>
        field = MutableStateFlow(false)

    fun setActive(value: Boolean) {
        active.value = value
    }
}
```

Within the supported private scope, the compiler knows the backing field's more specific type. External callers see StateFlow and cannot assign its value through that API.

This controls the exposed mutation surface; it does not turn MutableStateFlow into an immutable object or make every public field safe to expose. Continue to use atomic updates when a new state depends on its previous value.

## References

- [Kotlin 2.4: explicit backing fields stabilization](https://kotlinlang.org/docs/whatsnew24.html)
- [Kotlin 2.3: field syntax and private-scope narrowing](https://kotlinlang.org/docs/whatsnew23.html)
