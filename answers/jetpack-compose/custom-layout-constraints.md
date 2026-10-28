# How do constraints flow through a custom `Layout`? Why is measuring a child repeatedly in one layout pass unsupported, and when are intrinsic measurements useful?

[Back to questions](../../README.md#jetpack-compose)

**Level:** Senior · **Topic:** Jetpack Compose

## Answer

A parent passes minimum and maximum width/height constraints to its children. A custom Layout measures children under chosen valid constraints, chooses its own constrained size, and places the resulting placeables. Size and position are related but separate decisions.

Ordinary Compose layout does not support repeatedly measuring the same child in one pass to try arbitrary candidate sizes. This keeps layout work predictable. Intrinsic measurements ask about a child's size requirements before the actual measurement when the parent genuinely needs that information.

Use built-in layouts first. Specialized APIs such as SubcomposeLayout address different composition/measurement dependencies, not a blanket permission for uncontrolled repeated measurement. Handle zero, bounded, and unbounded constraints, and test font scaling and right-to-left placement in custom layouts.

## References

- [Android: custom layouts](https://developer.android.com/develop/ui/compose/layouts/custom)
- [Android: intrinsic measurements](https://developer.android.com/develop/ui/compose/layouts/intrinsic-measurements)
