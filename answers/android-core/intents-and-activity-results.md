# Explicit vs. implicit intents. What is the Activity Result API used for?

[Back to questions](../../README.md#android-core)

**Level:** Junior · **Topic:** Android Core

## Answer

An explicit intent names the receiving component. An implicit intent describes an action and optional data; Android resolves it against matching exported components and intent filters. Use explicit intents for known internal destinations and validate externally supplied data.

The Activity Result API separates registering a result callback from launching an operation through a contract, such as selecting content or requesting permissions. Register callbacks consistently during component initialization so they can be restored correctly; launch only when the lifecycle permits it.

A contract gives typed inputs and outputs and removes fragile request-code dispatch. A result can be absent or cancelled, and the process may be recreated while another app is open. Do not keep the pending operation's only important state in a local variable.

## References

- [Android: intents](https://developer.android.com/guide/components/intents-filters)
- [Android: Activity Result API](https://developer.android.com/training/basics/intents/result)
