# What is a composable function? How does declarative UI differ from updating Views directly?

[Back to questions](../../README.md#jetpack-compose)

**Level:** Junior · **Topic:** Jetpack Compose

## Answer

A composable function describes part of a UI from its inputs and observable state. The Compose compiler and runtime manage its participation in the composition; a composable is not simply an ordinary function returning a View.

```kotlin
@Composable
fun Greeting(name: String) {
    Text(text = "Hello, $name")
}
```

With Views, code commonly mutates an existing widget when data changes. With Compose, update state and let the runtime update the relevant UI description. Composables can be invoked repeatedly, skipped, or have a composition attempt discarded. Keep their bodies free of uncontrolled external side effects: use event callbacks and effect APIs for work such as navigation, subscriptions, and I/O.

## References

- [Android: thinking in Compose](https://developer.android.com/develop/ui/compose/mental-model)
