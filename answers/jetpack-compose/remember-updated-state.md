# When would you use `rememberUpdatedState` to avoid a stale value in a long-running effect?

[Back to questions](../../README.md#jetpack-compose)

**Level:** Middle · **Topic:** Jetpack Compose

## Answer

`rememberUpdatedState` keeps a stable State holder whose value is updated on recomposition. A long-running effect can read the latest callback or configuration without restarting its operation.

```kotlin
val latestOnFinished by rememberUpdatedState(onFinished)
LaunchedEffect(operationId) {
    performOperation(operationId)
    latestOnFinished()
}
```

The operation restarts if `operationId` changes, but replacing `onFinished` alone updates the callback used when it completes. Without this pattern, a callback captured when the effect started can become stale.

Do not use it to hide a real work-identity change. If a changed input means the old request must be cancelled and a new one started, that input belongs in the effect's keys. Lifecycle and error handling are still separate responsibilities.

## References

- [Android: rememberUpdatedState](https://developer.android.com/develop/ui/compose/side-effects#rememberupdatedstate)
