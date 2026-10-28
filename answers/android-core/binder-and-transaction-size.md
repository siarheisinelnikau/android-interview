# What does Binder do? Compare `Parcelable` and `Serializable`, and explain how oversized transactions can fail.

[Back to questions](../../README.md#android-core)

**Level:** Middle · **Topic:** Android Core

## Answer

Binder provides Android's interprocess communication mechanism. A remote call marshals data across a process boundary and may block, fail, or encounter a dead remote process; it is not equivalent to calling an ordinary local object.

`Parcelable` is Android's explicit transport-oriented serialization contract; Kotlin's Parcelize plugin can generate implementations. `Serializable` is Java's general object serialization mechanism. Neither makes sending a large object safe.

Binder uses a limited shared transaction buffer, so several simultaneous transactions and saved-state payloads can contribute to `TransactionTooLargeException`. There is no safe rule that every payload just below the advertised process buffer size will succeed. Pass small IDs or content URIs and load large data separately. Keep saved-state Bundles small and avoid transporting bitmaps or complete datasets.

## References

- [Android: Binder](https://developer.android.com/reference/android/os/Binder)
- [Android: TransactionTooLargeException](https://developer.android.com/reference/android/os/TransactionTooLargeException)
- [Kotlin: Parcelize](https://developer.android.com/kotlin/parcelize)
