# When are nested type aliases useful? Do they introduce a new type or capture an outer class's type parameters?

[Back to questions](../../README.md#kotlin-versions)

**Level:** Middle · **Topic:** Kotlin Versions · **Version:** Kotlin 2.3 · **Reviewed:** 2026-10-29

## Answer

Nested type aliases became stable in Kotlin 2.3. They keep an implementation-specific shorthand near the class, interface, or object that owns it, reducing package-level clutter.

An alias still expands to the same underlying type; it does not establish a new domain identity. A nested alias cannot capture type parameters from its outer class. If a generic parameter is needed, declare it on the alias itself within the supported rules.

Visibility also matters: an alias cannot expose a less visible underlying type, and its container limits where it is accessible. Use a value class when a distinct compile-time domain type is required, rather than expecting a nested alias such as UserId = Long to prevent mixing it with another Long alias.

## References

- [Kotlin: nested type aliases](https://kotlinlang.org/docs/type-aliases.html)
- [Kotlin 2.3: stabilization](https://kotlinlang.org/docs/whatsnew23.html)
