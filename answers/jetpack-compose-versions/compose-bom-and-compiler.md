# How does the Compose BOM align Runtime, UI, and Material 3 artifacts with different version numbers? Why is the compiler plugin configured separately?

[Back to questions](../../README.md#jetpack-compose-versions)

**Level:** Middle · **Topic:** Jetpack Compose Versions · **Reviewed:** 2026-10-28

## Answer

The Compose BOM supplies a tested set of compatible library versions, allowing Runtime, UI, Foundation, and Material dependencies to omit individual version numbers. Their version numbers need not be identical. A BOM constrains versions; it does not automatically add every library as a dependency.

The Compose compiler is coupled to the Kotlin compiler rather than the runtime release cadence. With Kotlin 2.0 and later, configure the Compose compiler Gradle plugin using the Kotlin version, separately from the BOM.

Update the BOM for the relevant configurations, including tests, and inspect the resolved dependency graph. An explicit library override can pull in newer transitive dependencies. Check compatibility instead of assuming that a single alpha override leaves the rest of the stack unchanged.

## References

- [Android: Compose BOM and compiler versioning](https://developer.android.com/develop/ui/compose/bom)
