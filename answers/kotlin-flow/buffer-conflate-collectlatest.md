# Compare `buffer`, `conflate`, and `collectLatest`. Which values or work can be skipped or cancelled?

[Back to questions](../../README.md#kotlin-flow)

**Level:** Middle · **Topic:** Kotlin Flow

## Answer

buffer lets upstream and downstream run in separate coroutines with a queue between them. With suspending overflow behavior, a full queue suspends the producer rather than dropping items. Capacity changes throughput, memory, and latency; it cannot solve unlimited sustained overload.

conflate skips intermediate pending values so a slow collector receives a more recent value. collectLatest instead cancels the previous collector action when a new value arrives, then processes the newest value.

Use these policies according to what may be skipped. Conflating progress updates can be reasonable; dropping financial operations is not. Cancelling a collector action does not roll back a network side effect already committed. The action must cooperate with cancellation for latest behavior to stop its local work promptly.

## References

- [kotlinx.coroutines: buffer](https://kotlinlang.org/api/kotlinx.coroutines/kotlinx-coroutines-core/kotlinx.coroutines.flow/buffer.html)
- [kotlinx.coroutines: conflate](https://kotlinlang.org/api/kotlinx.coroutines/kotlinx-coroutines-core/kotlinx.coroutines.flow/conflate.html)
- [kotlinx.coroutines: collectLatest](https://kotlinlang.org/api/kotlinx.coroutines/kotlinx-coroutines-core/kotlinx.coroutines.flow/collect-latest.html)
