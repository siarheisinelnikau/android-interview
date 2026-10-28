# Runtime 1.9 - what do `@RememberInComposition` and `@FrequentlyChangingValue` help lint detect? Why move stability annotations into `runtime-annotation`?

[Back to questions](../../README.md#jetpack-compose-versions)

**Level:** Middle · **Topic:** Jetpack Compose Versions · **Reviewed:** 2026-10-29

## Answer

Runtime 1.9 introduced tooling annotations that make common Compose misuse visible to lint. `@RememberInComposition` marks declarations whose results should be remembered when called during composition. `@FrequentlyChangingValue` warns about direct composition reads likely to cause very frequent recompositions, such as rapidly changing UI values.

The separate `runtime-annotation` artifact lets modules expose relevant contracts, including stability annotations, without depending on the full Compose runtime. Moving an annotation's artifact does not mean every annotated type needs to become a composable.

Treat diagnostics as a prompt to inspect ownership and observation. Remembering the wrong lifetime or moving a read to an inappropriate phase can still be incorrect. Match AGP/Lint support to the library's documented requirements so the checks actually run.

## References

- [Android Developers: August 2025 Compose annotations](https://android-developers.googleblog.com/2025/08/whats-new-in-jetpack-compose-august-25-release.html)
