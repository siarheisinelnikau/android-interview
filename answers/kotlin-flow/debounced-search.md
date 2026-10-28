# How would you implement search with `debounce`, `distinctUntilChanged`, and `flatMapLatest`?

[Back to questions](../../README.md#kotlin-flow)

**Level:** Middle · **Topic:** Kotlin Flow

## Answer

Normalize input, suppress repeated equivalent queries, wait for a short quiet period, then replace obsolete searches. Keep expected request errors inside the inner flow so one failed request does not permanently end future query handling.

```kotlin
queries.map { it.trim() }
    .distinctUntilChanged()
    .debounce(300)
    .flatMapLatest { query ->
        repository.search(query)
            .catch { e ->
                if (e is IOException) emit(SearchState.Failed)
                else throw e
            }
    }
```

This assumes search returns a Flow<SearchState>; handle blank input and loading states deliberately. Some operators require opt-ins depending on the library version. Cancellation must reach the actual request, and already committed server effects cannot be rolled back by latest collection. Decide whether clearing input should update immediately rather than waiting for the debounce interval.

## References

- [kotlinx.coroutines: debounce](https://kotlinlang.org/api/kotlinx.coroutines/kotlinx-coroutines-core/kotlinx.coroutines.flow/debounce.html)
- [kotlinx.coroutines: latest flattening](https://kotlinlang.org/api/kotlinx.coroutines/kotlinx-coroutines-core/kotlinx.coroutines.flow/flat-map-latest.html)
