# How would you handle navigation and snackbar actions across lifecycle changes? Discuss state, delivery guarantees, and the risks of one-off event streams.

[Back to questions](../../README.md#patterns-and-architecture)

**Level:** Senior · **Topic:** Patterns and Architecture

## Answer

Decide whether an action is ephemeral presentation or the consequence of a durable business state change. A snackbar may tolerate an explicit display policy; a completed purchase must remain recorded independently of whether a screen was collecting an event stream.

A SharedFlow without replay can lose emissions when no collector is active. Replay can re-deliver an already handled action after recreation. A Channel also does not by itself guarantee that a received action was completed before cancellation.

For important outcomes, expose state with an identifier and explicit acknowledgment or reconstruct the UI from a durable operation record. Make handling idempotent where appropriate. UI-local navigation can be handled by its navigation owner. No in-memory primitive alone provides exactly-once business execution across process death.

## References

- [Android: handling UI events](https://developer.android.com/topic/architecture/ui-layer/events)
