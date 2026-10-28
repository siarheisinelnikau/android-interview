# Why can mutating a regular list inside `mutableStateOf` fail to update the UI? Compare immutable updates and snapshot state collections.

[Back to questions](../../README.md#jetpack-compose)

**Level:** Middle · **Topic:** Jetpack Compose

## Answer

`mutableStateOf` observes assignments to its value according to its mutation policy; it does not instrument arbitrary mutations inside the referenced object. A plain MutableList can change without producing a state write, leaving the UI unaware.

```kotlin
var items by mutableStateOf(listOf<String>())
items = items + "new item" // New immutable snapshot.

val observedItems = mutableStateListOf<String>()
observedItems.add("another item") // Observable structural mutation.
```

Choose immutable state snapshots or snapshot-aware collections consistently. A snapshot list observes list operations, not arbitrary mutations of non-observable fields inside an element. Those element changes still need observable state or replacement values. Equality matters too: assigning a value considered equivalent by the state policy may intentionally avoid invalidation.

## References

- [Android: observable state and collection pitfalls](https://developer.android.com/develop/ui/compose/state)
