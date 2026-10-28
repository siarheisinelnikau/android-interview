# How would you assess a move from Runtime 1.12 to a 1.13 beta? Does a stable library release guarantee every API is stable?

[Back to questions](../../README.md#jetpack-compose-versions)

**Level:** Senior · **Topic:** Jetpack Compose Versions · **Reviewed:** 2026-10-28

## Answer

A stable artifact can contain individually experimental APIs, and a beta artifact can include changes whose compatibility is not yet final. Check the status of the specific symbols and flags you use, not only the artifact's version suffix.

For a move from Runtime 1.12 to a 1.13 beta, review release notes and compatibility requirements, inspect resolved dependencies, and isolate the upgrade in a small change. Run representative navigation, state restoration, effect-cancellation, and UI tests, then compare performance in a release-like build.

Keep an explicit rollback path and avoid combining a runtime upgrade with unrelated architecture changes that hide the source of regressions. Opt-in is a compatibility commitment the team should understand; it is not proof that a feature is unsuitable or production-ready.

## References

- [Android: Compose Runtime releases and API status](https://developer.android.com/jetpack/androidx/releases/compose-runtime)
