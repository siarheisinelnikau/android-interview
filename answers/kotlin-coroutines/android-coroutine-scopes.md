# Compare `viewModelScope`, `lifecycleScope`, and an application-owned scope. Why is `GlobalScope` usually discouraged?

[Back to questions](../../README.md#kotlin-coroutines)

**Level:** Middle · **Topic:** Kotlin Coroutines

## Answer

`viewModelScope` follows a ViewModel and is cancelled when it is cleared, making it appropriate for screen-level work that survives configuration recreation. `lifecycleScope` follows a LifecycleOwner and ends at destruction; a Fragment's UI work often needs its viewLifecycleOwner instead of the Fragment instance.

An application-owned scope can intentionally outlive a screen for in-process work, provided its error policy, shutdown, and tests are explicit. It still cannot survive process termination; use persistent scheduling and storage when that is required.

GlobalScope has no useful local owner and makes completion, cancellation, and testing harder to coordinate. Avoid choosing it merely because a request should survive a rotation. First determine whether the proper owner is a ViewModel, application component, service, or persistent worker.

## References

- [Android: lifecycle-aware coroutine scopes](https://developer.android.com/topic/libraries/architecture/coroutines)
- [kotlinx.coroutines: GlobalScope](https://kotlinlang.org/api/kotlinx.coroutines/kotlinx-coroutines-core/kotlinx.coroutines/-global-scope/)
