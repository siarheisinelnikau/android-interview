# `val` vs. `var`. Why does `val` not guarantee that an object is immutable?

[Back to questions](../../README.md#kotlin)

**Level:** Junior · **Topic:** Kotlin

## Answer

`var` exposes reassignment through a setter; `val` exposes reading without a setter. Neither keyword alone describes whether the referenced object can mutate.

```kotlin
val names = mutableListOf("Ada")
names.add("Lin") // Allowed: the list changes, not the reference.
```

A `val` with a custom getter can even return a different value on each access. Deep immutability requires the complete reachable state to follow an immutable contract, not merely read-only property declarations.

Prefer the narrowest mutability needed and expose read-only interfaces to callers where useful. A private mutable implementation can be appropriate, but if callers retain another mutable alias, they can still observe changes. Thread safety and safe publication are separate requirements.

## References

- [Kotlin: properties](https://kotlinlang.org/docs/properties.html)
