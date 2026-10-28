# Why does a version catalog not enforce the resolved version? Compare a BOM, `platform`, `enforcedPlatform`, and dependency constraints.

[Back to questions](../../README.md#gradle-and-gradle-dsl)

**Level:** Middle · **Topic:** Gradle and Gradle DSL · **Reviewed:** 2026-10-29

## Answer

A version catalog supplies aliases and declared version requests. Resolution can still select a different version because of another dependency or constraint. Catalogs reduce declaration duplication; they are not a universal version lock.

A platform provides a set of dependency constraints. A Maven BOM can be imported as a platform, and a java-platform project can define your own constraints. A constraint influences a module's version when that module participates in the graph; it does not add the module by itself.

An enforcedPlatform forces the platform's versions and can impose those choices transitively on consumers, so be careful when publishing a reusable library. A regular platform and explicit strict constraints have different semantics. Inspect the resolved graph rather than reading only `libs.versions.toml`. Version alignment, locking the chosen graph, and verifying the downloaded bytes are three separate requirements.

## References

- [Gradle: catalogs and resolution](https://docs.gradle.org/current/userguide/version_catalogs.html)
- [Gradle: platforms and enforced platforms](https://docs.gradle.org/current/userguide/platforms.html)
- [Gradle: constraints](https://docs.gradle.org/current/userguide/dependency_constraints.html)
