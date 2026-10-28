# State hoisting and unidirectional data flow - where should screen state and reusable component state live?

[Back to questions](../../README.md#jetpack-compose)

**Level:** Middle · **Topic:** Jetpack Compose

## Answer

Hoist state to the lowest common owner that needs to read or change it, then expose values downward and events upward. A reusable component normally accepts a value and callback; it should not create an unrelated screen ViewModel internally.

```kotlin
@Composable
fun FilterRow(enabled: Boolean, onEnabledChange: (Boolean) -> Unit) {
    Switch(checked = enabled, onCheckedChange = onEnabledChange)
}
```

Screen state and business decisions often belong in a ViewModel, while purely local UI details may stay in a composable or a plain state holder. Keep one source of truth for a value. Hoisting everything to the top unnecessarily increases coupling; duplicating the same editable state in several owners creates synchronization bugs.

## References

- [Android: state hoisting](https://developer.android.com/develop/ui/compose/state-hoisting)
