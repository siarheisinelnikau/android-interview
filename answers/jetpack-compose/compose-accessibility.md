# How do semantics, touch targets, focus order, and content descriptions affect accessibility?

[Back to questions](../../README.md#jetpack-compose)

**Level:** Middle · **Topic:** Jetpack Compose

## Answer

Semantics describe a component's meaning, role, state, and actions to accessibility services and tests. Standard components provide much of this behavior; custom drawing or gesture code needs equivalent semantics and accessible actions.

Describe meaningful unlabeled images and mark decorative images appropriately rather than repeating adjacent text. Provide suitable touch targets, logical focus/traversal order, state descriptions, and alternatives to gesture-only interactions. Merge semantics when several visual nodes form one user-facing control, without hiding independent actions.

Verify with TalkBack, keyboard or switch-style navigation, large text, and high-contrast scenarios where relevant. Content descriptions alone do not make an interface accessible: a label that cannot be reached, activated, or understood in its current state still fails the user's task.

## References

- [Android: Compose semantics](https://developer.android.com/develop/ui/compose/accessibility/semantics)
- [Android: accessibility practices](https://developer.android.com/develop/ui/compose/accessibility/api-defaults)
