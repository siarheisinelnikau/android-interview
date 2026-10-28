# How do `runTest`, test dispatchers, and a shared `TestCoroutineScheduler` make coroutine tests deterministic?

[Back to questions](../../README.md#testing)

**Level:** Middle · **Topic:** Testing

## Answer

runTest provides a test scope and scheduler that can control virtual time for work running on compatible test dispatchers. StandardTestDispatcher queues execution until the test yields or advances the scheduler; UnconfinedTestDispatcher can eagerly enter some coroutines but should not be treated as a universal production-order simulator.

```kotlin
@Test
fun delayedValue() = runTest {
    val deferred = async { delay(1_000); 42 }
    advanceUntilIdle()
    assertEquals(42, deferred.await())
}
```

Share one TestCoroutineScheduler across injected test dispatchers, and replace/reset Main when the tested Android owner requires it. Real I/O, ordinary thread sleeps, and work on unrelated dispatchers are not automatically virtualized. Put intentionally long-lived collectors in an appropriate background test scope and verify cancellation instead of letting a never-ending job hang the test.

## References

- [Android: coroutine testing](https://developer.android.com/kotlin/coroutines/test)
