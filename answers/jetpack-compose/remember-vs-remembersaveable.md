# Compare `remember` and `rememberSaveable`. What happens after recreation or process death?

[Back to questions](../../README.md#jetpack-compose)

**Level:** Junior · **Topic:** Jetpack Compose

## Answer

`remember` stores a value at an identity in the composition and reuses it across recompositions. It is forgotten when that identity leaves composition; it does not itself survive Activity recreation.

`rememberSaveable` participates in the saved-state system, using supported values or a custom Saver. It can restore appropriate UI state across recreation and supported system-initiated process restoration. It is not durable storage and does not promise restoration after a user dismisses the task or force-stops the app.

```kotlin
var query by rememberSaveable { mutableStateOf("") }
```

Keep small reconstruction inputs here, not large result lists or resources. Changing inputs/keys can reset remembered state; a ViewModel has a different owner and lifetime from either of these functions.

## References

- [Android: Compose state saving](https://developer.android.com/develop/ui/compose/state-saving)
