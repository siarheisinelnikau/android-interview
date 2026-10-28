# How do call-site identity and `key` affect remembered state when composables are reordered or conditionally included?

[Back to questions](../../README.md#jetpack-compose)

**Level:** Middle · **Topic:** Jetpack Compose

## Answer

Compose identifies calls using their call site and execution position; keys can provide additional identity when items move or are conditionally included. Remembered state and running effects belong to that identity, not to the textual value displayed on screen.

```kotlin
for (item in items) {
    key(item.id) { EditableItem(item) }
}
```

Without stable item identity, reordering can associate local state with the wrong position or restart effects unnecessarily. A lazy list has its own item-key parameter for this purpose.

A key must distinguish siblings at that call site and remain stable for the logical item. A random value or list position usually defeats that goal. Keys preserve identity while the relevant composition is retained; they do not make removed state persist forever.

## References

- [Android: composable identity and key](https://developer.android.com/develop/ui/compose/lifecycle)
