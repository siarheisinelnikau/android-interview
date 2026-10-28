# What bugs can the experimental unused return value checker detect? How would you introduce it without hiding meaningful warnings?

[Back to questions](../../README.md#kotlin-versions)

**Level:** Senior · **Topic:** Kotlin Versions · **Version:** Kotlin 2.3 · **Reviewed:** 2026-10-28

## Answer

The experimental unused return value checker can catch code that computes a meaningful result and then ignores it. A typical bug is calling `items.filter { ... }` as though it mutated the original collection, or discarding a result whose failure needs handling.

In Kotlin 2.3, the documented compiler options include `-Xreturn-value-checker=check` for marked scopes and `full` for broader project checking. Relevant annotations can mark results as significant or intentionally ignorable. Check the exact release's experimental setup before enabling it.

Introduce it in a limited module, inspect findings, and document intentional exceptions. Do not blanket-suppress warnings just to get a green build. Conversely, an ignored value is not automatically a bug; side-effecting APIs and domain conventions still require judgment.

## References

- [Kotlin 2.3: unused return value checker](https://kotlinlang.org/docs/whatsnew23.html)
