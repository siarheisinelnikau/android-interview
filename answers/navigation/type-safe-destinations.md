# How would you model type-safe destinations and pass identifiers instead of large objects between screens?

[Back to questions](../../README.md#navigation)

**Level:** Middle · **Topic:** Navigation

## Answer

Represent a destination with a typed route containing the small arguments needed to identify it. With supported Navigation Compose versions, Kotlin serialization can define type-safe routes; Navigation 3 can use serializable destination keys with an application-owned stack.

```kotlin
@Serializable
data class ProductRoute(val productId: Long)
```

The destination loads the current product by ID instead of receiving a large stale Product object. This keeps transport small, supports restoration and deep links, and preserves a single data source.

Validate external IDs and authorization after navigation. A typed ID does not prove the user can access the object. Avoid secrets and large mutable models in routes, and define a clear not-found or unavailable state when the referenced data no longer exists.

## References

- [Android: type-safe navigation](https://developer.android.com/guide/navigation/design/type-safety)
