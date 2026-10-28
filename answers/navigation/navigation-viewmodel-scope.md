# How do you scope a `ViewModel` to a destination or navigation graph and restore navigation state?

[Back to questions](../../README.md#navigation)

**Level:** Middle · **Topic:** Navigation

## Answer

Scope a ViewModel to the owner matching the intended state lifetime. A destination-owned instance ends when that entry is permanently removed; a graph-owned instance can share state across the graph's destinations. An Activity-owned instance can outlive several screens and unintentionally share their state.

In Navigation Compose, obtain the intended back-stack entry as the ViewModelStore owner. In Navigation 3, install the ViewModel-store entry decorator together with the required saveable-state decorator when configuring custom decorators. Calling `viewModel()` alone does not guarantee destination scope.

Save small route and UI reconstruction values through supported saved-state mechanisms. ViewModel retention only covers configuration changes; after process death a new instance must reconstruct state from saved inputs and persistent data.

## References

- [Android: navigation ViewModel sharing](https://developer.android.com/guide/navigation/use-graph/programmatic)
- [Android: Navigation 3 state and ViewModel decorators](https://developer.android.com/guide/navigation/navigation-3/save-state)
