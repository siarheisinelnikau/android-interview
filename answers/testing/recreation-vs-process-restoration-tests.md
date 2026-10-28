# How would you test a screen's restoration after recreation and after process death? What does `ActivityScenario.recreate()` actually cover?

[Back to questions](../../README.md#testing)

**Level:** Middle · **Topic:** Testing

## Answer

ActivityScenario.recreate() destroys and recreates the Activity in the same process. It exercises configuration-style restoration but can retain ViewModels and all other surviving process memory. It therefore does not prove recovery after process death.

For process restoration, create meaningful state, background the app so supported saved state can be recorded, terminate the background process with an appropriate test harness, and return to the task. Verify that new instances reconstruct the screen from saved inputs and durable data. Force-stop and clearing app data have different semantics and are not interchangeable simulations.

Test small saved UI state separately with supported saved-state/Compose restoration helpers, then keep an integration scenario for the full path. Include incomplete operations and unavailable cached data so restoration does not accidentally rely on a singleton from the earlier process.

## References

- [Android: ActivityScenario recreate contract](https://developer.android.com/reference/androidx/test/core/app/ActivityScenario)
- [Android: UI state restoration](https://developer.android.com/topic/libraries/architecture/saving-states)
