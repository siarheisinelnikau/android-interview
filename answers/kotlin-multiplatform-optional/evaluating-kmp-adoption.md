# How would you evaluate library support, platform interop, testing, and build complexity before moving an Android feature into shared code?

[Back to questions](../../README.md#kotlin-multiplatform-optional)

**Level:** Senior · **Topic:** Kotlin Multiplatform (Optional)

## Answer

Start with a cohesive feature whose domain behavior can be tested independently, then inventory its platform dependencies. Check target support and maturity for networking, storage, DI, serialization, and UI before moving code. A library supporting JVM is not automatically usable from commonMain or Kotlin/Native.

Prototype the platform boundary, error/cancellation mapping, Swift or other language interop, and the development/build workflow. Include CI, debugging, test execution, binary size, and ownership by both platform teams in the evaluation.

Move a small vertical slice and compare maintenance cost and behavior before expanding. Keep platform-specific capabilities behind clear contracts and preserve a fallback if an integration is immature. Shared code can reduce duplicated rules, but it also creates a shared release and compatibility responsibility that must be worthwhile for the team.

## References

- [Kotlin: Multiplatform project structure](https://kotlinlang.org/docs/multiplatform/multiplatform-discover-project.html)
- [Kotlin: platform-specific APIs](https://kotlinlang.org/docs/multiplatform/multiplatform-connect-to-apis.html)
