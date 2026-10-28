# How do the stabilized annotation defaulting rules and `@all` meta-target affect constructor properties used by Android or validation frameworks?

[Back to questions](../../README.md#kotlin-versions)

**Level:** Middle · **Topic:** Kotlin Versions · **Version:** Kotlin 2.4 · **Reviewed:** 2026-10-28

## Answer

Kotlin 2.4 stabilizes the revised default annotation-target rules and the `@all` property meta-target. A Kotlin constructor property can correspond to several generated elements; an annotation seen on one does not imply it appears on every other element.

The new defaulting rules can propagate to more than one applicable parameter/property/field target. `@all` applies an annotation to the supported applicable elements of a property; it does not mean every possible Kotlin declaration target. Annotation retention and allowed targets still constrain the result.

For validation, persistence, or Android tooling, verify which element the framework inspects and check generated output. Use explicit `@field:`, `@get:`, or `@param:` when the contract needs precision. Test upgrades instead of assuming old implicit placement remains unchanged.

## References

- [Kotlin: annotation targets and all meta-target](https://kotlinlang.org/docs/annotations.html)
- [Kotlin 2.4: annotation feature stabilization](https://kotlinlang.org/docs/whatsnew24.html)
