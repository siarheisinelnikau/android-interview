# Why can nesting a `LazyColumn` inside another vertically scrolling container fail with unbounded constraints? How would you structure the content?

[Back to questions](../../README.md#jetpack-compose)

**Level:** Middle · **Topic:** Jetpack Compose

## Answer

A vertically scrolling parent can measure content with unbounded height. A nested lazy vertical list then has no finite viewport to decide which items to compose, and can fail a scrollable-constraint check. This is a measurement problem, not merely a missing nested-scroll connection.

Often the correct design is one LazyColumn containing header items, content rows, and footer items. If independently scrolling regions are intentional, give each a meaningful bounded viewport, such as a constrained pane or explicitly sized child.

Orthogonal scrolling, such as a horizontal row inside a vertical list, has different constraints and is commonly valid. Do not fix the crash with an arbitrary enormous height: it can remove laziness, hide accessibility issues, and create unstable behavior on different windows.

## References

- [Android: lazy layout nesting](https://developer.android.com/develop/ui/compose/lists)
