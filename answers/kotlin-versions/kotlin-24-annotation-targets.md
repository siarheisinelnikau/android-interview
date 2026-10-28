# How do the stabilized annotation defaulting rules and `@all` meta-target affect constructor properties used by Android or validation frameworks?

[Back to questions](../../README.md#kotlin-versions)

**Level:** Middle · **Topic:** Kotlin Versions · **Version:** Kotlin 2.4 · **Reviewed:** 2026-10-29

## Answer

Kotlin 2.4 stabilizes the revised default annotation-target rules and `@all`. For an annotation without an explicit use-site target, applicable targets include the constructor parameter plus the property; if the annotation cannot target the property, the backing field is considered instead. A property supporting both parameter and field targets can therefore receive **both**, rather than the older first-applicable-target behavior.

`@all:Annotation` propagates to supported applicable elements: constructor parameter, property, backing field, getter, and the setter **parameter** for a `var`, plus a record component where applicable. It does not annotate every possible target, including the setter method itself. Allowed targets, retention, and whether those generated elements exist still matter.

For validation or persistence, check which element the framework inspects. Use explicit `@field:`, `@get:`, or `@param:` for a precise contract, inspect generated output, and test for changed or duplicate validation after upgrading. A stable syntax feature does not make annotation consumers behave identically.

## References

- [Kotlin: annotation targets and all meta-target](https://kotlinlang.org/docs/annotations.html)
- [Kotlin 2.4: annotation feature stabilization](https://kotlinlang.org/docs/whatsnew24.html)
