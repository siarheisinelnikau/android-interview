# Compare `LaunchedEffect`, `DisposableEffect`, and `rememberCoroutineScope`. How do effect keys control cancellation and restarts?

[Back to questions](../../README.md#jetpack-compose)

**Level:** Middle · **Topic:** Jetpack Compose

## Answer

`LaunchedEffect` starts a coroutine owned by its composition identity and keys. It is cancelled when that identity leaves composition or when its keys change, then restarted for the new keys. `DisposableEffect` manages synchronous setup/cleanup for resources such as listeners. `rememberCoroutineScope` supplies a composition-owned scope for launching work in event callbacks.

Choose keys representing the work's identity, not every value mentioned by the code. Missing keys can preserve obsolete work, while overly broad keys restart work unnecessarily. Use `rememberUpdatedState` when a changing value should be read without restarting the effect.

Do not start a coroutine directly from the composable body on every execution. Effect ownership follows composition; a retained composition can still exist while an Activity is stopped, so lifecycle-aware APIs may also be needed.

## References

- [Android: Compose effect APIs](https://developer.android.com/develop/ui/compose/side-effects)
