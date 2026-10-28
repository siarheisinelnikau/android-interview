# What does `@OptIn` mean? How would you evaluate the stability and compatibility of a Kotlin API before adopting it?

[Back to questions](../../README.md#kotlin)

**Level:** Middle · **Topic:** Kotlin

## Answer

`@OptIn` records that code intentionally uses an API marked by an opt-in requirement. The marker describes compatibility or behavioral risk; opting in does not stabilize the API or guarantee that a future upgrade will compile.

Keep opt-ins near the smallest relevant boundary and read the marker's documentation. Some language features use compiler flags instead of, or in addition to, annotation-based API opt-ins. A stable artifact can contain experimental symbols.

Before adoption, check the exact release, compatibility guarantees, alternatives, downstream consumers, and rollback cost. For a library, exposing an experimental type can transfer obligations to callers. Review release notes and re-run relevant behavior tests on upgrades rather than suppressing warnings project-wide without tracking why they exist.

## References

- [Kotlin: opt-in requirements](https://kotlinlang.org/docs/opt-in-requirements.html)
- [Kotlin: language evolution](https://kotlinlang.org/docs/kotlin-evolution-principles.html)
