# How would you investigate touch dispatch or nested scrolling problems in a custom View hierarchy?

[Back to questions](../../README.md#android-ui-views)

**Level:** Senior · **Topic:** Android UI (Views)

## Answer

Trace the gesture from `dispatchTouchEvent` through parent interception and the selected child's `onTouchEvent`. Returning true claims handling; a parent that intercepts after a child started receives the rest of the gesture while the child receives cancellation. Incorrect handling of DOWN, MOVE, UP, or CANCEL often explains a broken gesture.

Check hit bounds, overlapping Views, touch slop, pointer changes, and `requestDisallowInterceptTouchEvent` behavior. Log a minimal gesture sequence rather than every event in a production build.

Nested scrolling is a separate coordination protocol for sharing scroll deltas between child and parent. Inspect pre-scroll, consumed distance, remaining distance, and fling behavior. Avoid swallowing all events at a parent as a quick fix; it can break child clicks, accessibility, and expected scrolling.

## References

- [Android: touch event handling in ViewGroups](https://developer.android.com/develop/ui/views/touch-and-input/gestures/viewgroup)
