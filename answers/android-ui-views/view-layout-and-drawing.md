# What are the measure, layout, and draw phases of a View? When would you use `requestLayout()` vs. `invalidate()`?

[Back to questions](../../README.md#android-ui-views)

**Level:** Middle · **Topic:** Android UI (Views)

## Answer

During measure, each View determines a size within its parent's MeasureSpecs. During layout, positions and bounds are assigned. During drawing, the hierarchy paints backgrounds, content, children, and decorations as appropriate.

Call `requestLayout()` when a change can affect size or placement, such as a changed intrinsic size. Call `invalidate()` when pixels must change without requiring new geometry, such as a custom indicator's color. Some property setters perform the required invalidation themselves.

Do not allocate large temporary objects or perform I/O inside `onDraw`. Cache expensive calculations when their inputs change and respond correctly to size changes. Excessive layout requests can trigger repeated hierarchy work, while failing to request layout can leave stale bounds even if drawing is invalidated.

## References

- [Android: custom drawing](https://developer.android.com/develop/ui/views/layout/custom-views/custom-drawing)
- [Android: View reference](https://developer.android.com/reference/android/view/View)
