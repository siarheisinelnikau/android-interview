# What changed with the stable K2 compiler? How would you investigate source compatibility or smart-cast changes during migration?

[Back to questions](../../README.md#kotlin-versions)

**Level:** Middle · **Topic:** Kotlin Versions · **Version:** Kotlin 2.0 · **Reviewed:** 2026-10-28

## Answer

Kotlin 2.0 made K2 the stable default compiler frontend across supported targets. It changes compiler analysis and enables further language development; it is not a new Android runtime or a promise that every application executes faster after recompilation.

During migration, compare diagnostics, inferred types, overload resolution, and smart-cast behavior against the compatibility guide. Reduce surprising failures to a small example, distinguish an intentional language change from a compiler bug, and check compiler plugins and generated code.

Upgrade tooling in a controlled change and measure build performance separately from runtime performance. Preserve meaningful tests around Java interop and public APIs. Changing the compiler version, language version, API version, and JVM bytecode target are related but distinct configuration choices.

## References

- [Kotlin: 2.0 and K2](https://kotlinlang.org/docs/whatsnew20.html)
- [Kotlin: K2 migration guide](https://kotlinlang.org/docs/k2-compiler-migration-guide.html)
