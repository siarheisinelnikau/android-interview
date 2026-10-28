# Nested vs. inner classes - which holds an outer instance, and how can that cause an Android memory leak?

[Back to questions](../../README.md#kotlin)

**Level:** Middle · **Topic:** Kotlin

## Answer

A nested class is associated with the enclosing class's namespace but does not automatically hold an enclosing instance. An `inner` class has access to a particular outer instance and retains a reference to it.

```kotlin
class ScreenOwner {
    class Configuration
    inner class Listener { fun owner() = this@ScreenOwner }
}
```

If a long-lived listener or background task retains an inner object whose outer object is an Activity, the destroyed Activity can remain reachable. Lambdas and anonymous objects can also capture the outer instance when they use it.

Use explicit dependencies and lifecycle-owned registrations. Removing `inner` is insufficient if a constructor property or callback still stores the same Activity indirectly. Inspect the actual retention path when diagnosing a leak.

## References

- [Kotlin: nested and inner classes](https://kotlinlang.org/docs/nested-classes.html)
