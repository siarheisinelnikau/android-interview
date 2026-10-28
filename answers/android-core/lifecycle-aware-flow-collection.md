# Why use `repeatOnLifecycle` or `collectAsStateWithLifecycle` to collect flows from the UI?

[Back to questions](../../README.md#android-core)

**Level:** Middle · **Topic:** Android Core

## Answer

A collector should run only while the UI needs it. `repeatOnLifecycle(STARTED)` starts a child block when the lifecycle reaches that state, cancels it below that state, and restarts it later. `collectAsStateWithLifecycle` provides the corresponding lifecycle-aware state collection for Compose.

```kotlin
viewLifecycleOwner.lifecycleScope.launch {
    viewLifecycleOwner.repeatOnLifecycle(Lifecycle.State.STARTED) {
        viewModel.uiState.collect { render(it) }
    }
}
```

Without this ownership, a stopped screen may continue processing data or access a destroyed binding. Separate concurrent collectors into child `launch` calls within the repeated block. Cancellation of the UI collector does not necessarily stop a shared upstream producer; its owning scope and sharing policy determine that behavior.

## References

- [Android: lifecycle-aware coroutines](https://developer.android.com/topic/libraries/architecture/coroutines)
- [Android: lifecycle-aware Compose state](https://developer.android.com/develop/ui/compose/state)
