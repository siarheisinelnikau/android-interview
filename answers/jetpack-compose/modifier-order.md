# Why does modifier order matter? Compare padding before and after `clickable` or `background`.

[Back to questions](../../README.md#jetpack-compose)

**Level:** Middle · **Topic:** Jetpack Compose

## Answer

Modifiers wrap and transform layout, input, drawing, and semantics in the order applied, so their order is part of the component's behavior.

```kotlin
Modifier.clickable(onClick = onClick).padding(16.dp)
Modifier.padding(16.dp).clickable(onClick = onClick)
```

In the first chain, padding is inside the clickable region; in the second, the outer padding is not part of that clickable modifier's region. Background and clipping order likewise determine which area is painted or clipped.

Read a modifier chain as nested behavior, not a set of unordered attributes. Layout constraints and accessibility minimum touch targets can also affect the effective interaction area. For reusable composables, accept a Modifier and apply it at the appropriate outer node so callers can control placement and behavior.

## References

- [Android: Compose modifiers](https://developer.android.com/develop/ui/compose/modifiers)
