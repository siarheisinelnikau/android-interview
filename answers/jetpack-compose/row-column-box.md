# Compare `Row`, `Column`, and `Box`. How do alignment, arrangement, and `weight` affect a layout?

[Back to questions](../../README.md#jetpack-compose)

**Level:** Junior · **Topic:** Jetpack Compose

## Answer

`Row` places children horizontally, `Column` vertically, and `Box` stacks or positions children within the same area. Arrangement controls distribution along a Row or Column's main axis; alignment controls its cross axis. Box alignment positions children within its available space.

```kotlin
Row(Modifier.fillMaxWidth()) {
    Text("Description", Modifier.weight(1f))
    Text("Price")
}
```

Here the weighted text receives the remaining horizontal space after the other child is measured. Weight is scoped to Row or Column and depends on meaningful available constraints; it is not a general property for every container. Understand incoming constraints before adding `fillMaxSize`, fixed dimensions, or weights, since a parent ultimately determines what space a child can use.

## References

- [Android: Compose layout basics](https://developer.android.com/develop/ui/compose/layouts/basics)
