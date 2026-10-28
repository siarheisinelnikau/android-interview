# What do `stateIn`, `shareIn`, and `SharingStarted.WhileSubscribed` do? Who owns the upstream coroutine?

[Back to questions](../../README.md#kotlin-flow)

**Level:** Middle · **Topic:** Kotlin Flow

## Answer

stateIn turns upstream into a shared StateFlow with a current value; shareIn produces a SharedFlow with configured replay. The supplied scope owns the sharing coroutine and determines when it can be cancelled or fail.

SharingStarted.WhileSubscribed starts upstream when subscribers appear and stops it after the configured absence timeout. Replay expiration is a separate setting; stopping upstream does not automatically mean the last state disappears immediately. A new subscriber can restart a cold upstream.

Choose timeouts to match cost and lifecycle behavior, not as a universal constant copied from a sample. Handle upstream errors before sharing when the UI needs an explicit error state. In tests, install a collector for WhileSubscribed flows; reading value alone may not activate their upstream work.

## References

- [kotlinx.coroutines: stateIn](https://kotlinlang.org/api/kotlinx.coroutines/kotlinx-coroutines-core/kotlinx.coroutines.flow/state-in.html)
- [kotlinx.coroutines: shareIn](https://kotlinlang.org/api/kotlinx.coroutines/kotlinx-coroutines-core/kotlinx.coroutines.flow/share-in.html)
- [kotlinx.coroutines: WhileSubscribed](https://kotlinlang.org/api/kotlinx.coroutines/kotlinx-coroutines-core/kotlinx.coroutines.flow/-sharing-started/-companion/-while-subscribed.html)
