# When would you choose the stable common `kotlin.uuid.Uuid` API over `java.util.UUID`? What would you check when migrating serialized identifiers?

[Back to questions](../../README.md#kotlin-versions)

**Level:** Middle · **Topic:** Kotlin Versions · **Version:** Kotlin 2.4 · **Reviewed:** 2026-10-29

## Answer

Use `kotlin.uuid.Uuid` when identifiers belong in common multiplatform code instead of depending on JVM-only `java.util.UUID`. Kotlin 2.4 stabilizes the main common API, but the documented V4/V7 generation functions remain experimental and need their relevant opt-in.

For an existing Android-only public API, retaining java.util.UUID can avoid unnecessary interop churn. Convert at a platform boundary when sharing logic, rather than leaking Java types into common source sets.

During migration, test text format, parsing of invalid input, byte ordering, serialization adapters, database keys, and equality across converted values. A shared 128-bit identifier concept does not mean every serializer accepts the same representation automatically. Verify whether existing stored IDs use canonical dashed text, another text form, or bytes before changing the type.

## References

- [Kotlin: UUID guide](https://kotlinlang.org/docs/uuids.html)
- [Kotlin 2.4: UUID stabilization and exceptions](https://kotlinlang.org/docs/whatsnew24.html)
