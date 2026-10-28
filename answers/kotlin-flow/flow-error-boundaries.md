# How do `catch`, `retry`, and `onCompletion` interact with upstream errors, downstream errors, and cancellation?

[Back to questions](../../README.md#kotlin-flow)

**Level:** Middle · **Topic:** Kotlin Flow

## Answer

catch handles exceptions from upstream of its position and can emit a fallback. It is transparent to downstream failures and does not normally catch the cancellation used to cancel collection. retry recollects upstream for matching failures, so side effects before the failure can run again.

onCompletion observes how collection ended, including cancellation and downstream failure; it is useful for observation and cleanup but not a general replacement for catch. Emitting a successful fallback from a failed completion path is not the same supported recovery mechanism.

Place recovery inside a latest-mapped request if later user inputs must continue after one request fails. Limit retries, preserve cancellation, and distinguish transient transport errors from invalid input or authentication failure. Make repeated upstream effects safe before adding retry.

## References

- [kotlinx.coroutines: catch](https://kotlinlang.org/api/kotlinx.coroutines/kotlinx-coroutines-core/kotlinx.coroutines.flow/catch.html)
- [kotlinx.coroutines: onCompletion](https://kotlinlang.org/api/kotlinx.coroutines/kotlinx-coroutines-core/kotlinx.coroutines.flow/on-completion.html)
- [kotlinx.coroutines: retry](https://kotlinlang.org/api/kotlinx.coroutines/kotlinx-coroutines-core/kotlinx.coroutines.flow/retry.html)
