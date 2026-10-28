# Compare `StateFlow` and `SharedFlow`: current value, replay, equality-based conflation, and slow collectors.

[Back to questions](../../README.md#kotlin-flow)

**Level:** Middle · **Topic:** Kotlin Flow

## Answer

StateFlow represents a current value, requires an initial value, and gives a new collector the current state. Equal updates are suppressed according to equals, and slow collectors may skip intermediate updates. Use immutable state values and an atomic update operation when a new value depends on the previous one.

SharedFlow broadcasts values with configurable replay, buffer capacity, and overflow behavior. It has no required initial value and is not inherently a state holder. Without subscribers, only replayed values are retained; extra buffer capacity is not an offline event queue.

Both are hot and do not normally complete. Choose based on state versus broadcast semantics, not a rule that every event belongs in SharedFlow. Neither primitive persists values across process death or guarantees exactly-once user action handling.

## References

- [kotlinx.coroutines: StateFlow](https://kotlinlang.org/api/kotlinx.coroutines/kotlinx-coroutines-core/kotlinx.coroutines.flow/-state-flow/)
- [kotlinx.coroutines: SharedFlow](https://kotlinlang.org/api/kotlinx.coroutines/kotlinx-coroutines-core/kotlinx.coroutines.flow/-shared-flow/)
