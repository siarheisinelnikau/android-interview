# Compare `animate*AsState`, `Animatable`, and `updateTransition`. How would you coordinate animations and handle interrupted gestures?

[Back to questions](../../README.md#jetpack-compose)

**Level:** Middle · **Topic:** Jetpack Compose

## Answer

Use `animate*AsState` for a simple value that should animate toward a changing target. It is convenient for declarative state changes without an imperative animation controller.

Use `Animatable` when gesture or coroutine code must start, stop, snap, or sequence an animation. It coordinates its running animations and supports interruption. Use `updateTransition` when several animated values belong to one logical state transition and should be driven together.

For a draggable card, update or snap during direct manipulation, then animate to a settled position after release. Handle cancellation and preserve the appropriate current value/velocity for the chosen animation specification. Avoid launching a new unowned animation on every recomposition, and profile whether animation state is being read in composition when only drawing or placement needs it.

## References

- [Android: value-based animation APIs](https://developer.android.com/develop/ui/compose/animation/value-based)
