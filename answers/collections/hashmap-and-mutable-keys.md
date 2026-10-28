# How does `HashMap` work? What happens with collisions or mutable keys?

[Back to questions](../../README.md#collections)

**Level:** Middle · **Topic:** Collections

## Answer

A hash map uses a key's hash to select a bucket and equality to distinguish entries within it. Different keys may share a bucket; a hash collision does not imply equality. Load factor and capacity determine when storage is expanded. Implementation details, including collision treeification, vary by runtime and should not be treated as an Android-wide API guarantee.

Keys must keep a consistent `equals`/`hashCode` relationship while stored. If a property participating in hashing changes, the entry can remain in its old bucket while lookup searches a new one.

```kotlin
data class Key(var id: Int)
val key = Key(1)
val map = hashMapOf(key to "value")
key.id = 2 // Subsequent lookup/removal is no longer reliable.
```

Prefer immutable key identities.

## References

- [Java: Map key constraints](https://docs.oracle.com/en/java/javase/25/docs/api/java.base/java/util/Map.html)
