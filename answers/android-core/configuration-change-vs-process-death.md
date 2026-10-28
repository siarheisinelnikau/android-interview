# Configuration change vs. process death - what happens to an Activity and its `ViewModel`?

[Back to questions](../../README.md#android-core)

**Level:** Middle · **Topic:** Android Core

## Answer

A configuration change normally recreates the Activity and its UI while a properly scoped `ViewModel` is retained. The replacement Activity reconnects to that ViewModel. Its `onCleared()` is not called merely because the device rotated.

System-initiated process death removes all in-memory objects, including ViewModels and singletons. A later restoration creates new instances; only persisted data and state saved through the supported saved-state mechanism can be reconstructed. A ViewModel is not a process-death persistence mechanism.

Save small reconstruction inputs such as an item ID or search query, then reload the full data. Do not depend on a final callback before termination. Finishing the screen and force-stopping the app are different cases from system restoration and have different state expectations.

## References

- [Android: ViewModel overview](https://developer.android.com/topic/libraries/architecture/viewmodel)
- [Android: saved-state module](https://developer.android.com/topic/libraries/architecture/viewmodel/viewmodel-savedstate)
