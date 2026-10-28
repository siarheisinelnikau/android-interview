# Objects, companion objects, and top-level declarations - when would you use each?

[Back to questions](../../README.md#kotlin)

**Level:** Junior · **Topic:** Kotlin

## Answer

An object declaration defines a named singleton instance with its own members. A companion object supplies members associated with a containing class, such as a factory; it is still an object, not simply Java static syntax. Top-level functions and properties belong to a package/file and are useful when behavior does not need an object receiver.

Use an object for a deliberate shared identity or stateless implementation, a companion for construction-related behavior or class-associated constants, and top-level declarations for straightforward utilities.

Avoid putting mutable application state into a global object merely for easy access. It complicates isolation and can leak lifecycle-owned objects. For Java callers, inspect generated APIs and add interop annotations where appropriate rather than assuming a companion member is automatically a static method.

## References

- [Kotlin: object and companion declarations](https://kotlinlang.org/docs/object-declarations.html)
