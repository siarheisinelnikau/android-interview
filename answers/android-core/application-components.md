# Core components: `Activity`, `Service`, `BroadcastReceiver`, and `ContentProvider`. What is the role of `Application`?

[Back to questions](../../README.md#android-core)

**Level:** Junior · **Topic:** Android Core

## Answer

An Activity hosts an interactive UI entry point. A Service represents ongoing or bound work without a UI; it is not itself a worker thread. A BroadcastReceiver handles a broadcast briefly, and a ContentProvider exposes structured data through a URI-based interface, often across processes.

`Application` represents process-level application state and is commonly used for dependency-container initialization. It is not an Activity and does not have a screen lifecycle. An app using several processes can have a separate Application instance in each process.

Declare components and their exposure intentionally. Components can be created by the system without a normal launcher flow, so do not assume that an Activity has already initialized global dependencies.

## References

- [Android: application fundamentals](https://developer.android.com/guide/components/fundamentals)
