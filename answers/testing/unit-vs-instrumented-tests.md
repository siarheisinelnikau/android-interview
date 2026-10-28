# Unit tests vs. instrumented tests. What belongs in each for an Android app?

[Back to questions](../../README.md#testing)

**Level:** Junior · **Topic:** Testing

## Answer

Local unit tests execute on the development machine's JVM and are fast for pure logic, reducers, mapping, and repositories using controlled dependencies. They do not automatically supply a real Android framework; use an appropriate simulation framework only when its behavior matches the test's goal.

Instrumented tests run on an Android device or emulator and cover framework integration, installed app behavior, UI interaction, and platform-specific contracts. They cost more time and environmental setup.

Choose the smallest environment that can reveal the failure. A formatter needs no device; permission behavior or real Activity restoration does. Keep tests focused on observable behavior rather than private method calls. Test doubles reduce scope, while a few integration tests verify that the real components and configuration actually fit together.

## References

- [Android: testing fundamentals](https://developer.android.com/training/testing/fundamentals)
