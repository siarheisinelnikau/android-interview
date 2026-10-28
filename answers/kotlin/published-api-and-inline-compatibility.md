# Why can a public inline function not freely access private implementation details? How does `@PublishedApi` affect compatibility?

[Back to questions](../../README.md#kotlin)

**Level:** Senior · **Topic:** Kotlin

## Answer

A public inline function's implementation is copied into code compiled in other modules. It cannot freely depend on private or internal declarations that those callers are not allowed to reference in the generated program.

`@PublishedApi` makes an internal declaration eligible for use by public inline code. Although Kotlin source callers still see an internal declaration, library authors must treat its binary shape as part of the externally consumed implementation contract.

Changing or removing such a helper can break callers already compiled against it. Changing inline logic also does not rewrite existing callers until they are recompiled. Keep public inline bodies small, avoid exposing unstable implementation details, and include ABI considerations when evolving a library rather than assuming internal always means harmless to change.

## References

- [Kotlin: PublishedApi contract](https://kotlinlang.org/api/core/kotlin-stdlib/kotlin/-published-api/)
