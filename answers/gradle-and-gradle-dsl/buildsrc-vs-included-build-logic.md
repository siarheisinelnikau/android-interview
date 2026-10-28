# When would you use `buildSrc` or an included `build-logic` build for convention plugins? Why avoid broad cross-project configuration?

[Back to questions](../../README.md#gradle-and-gradle-dsl)

**Level:** Middle · **Topic:** Gradle and Gradle DSL · **Reviewed:** 2026-10-29

## Answer

buildSrc is a special build whose compiled build logic is automatically available to the main build. An included build is an explicit independent build, often named build-logic, that can supply convention plugins through plugin management. Both can host precompiled script or binary plugins.

Choose based on ownership, dependency isolation, plugin reuse, and measured change impact. An included build has its own settings, dependencies, and catalogs; the main build's `libs` accessor is not automatically its catalog. Import shared catalog data explicitly when appropriate, without turning every build decision into a global dependency.

Apply conventions in the projects that need them rather than mutating arbitrary sibling projects through allprojects/subprojects blocks. Cross-project model access introduces order coupling and conflicts with stronger project isolation. An included build is not automatically faster in every workload: measure configuration, build-logic recompilation, and affected task work before restructuring the whole repository.

## References

- [Gradle: sharing build logic with buildSrc](https://docs.gradle.org/current/userguide/sharing_build_logic_between_subprojects.html)
- [Gradle: included builds](https://docs.gradle.org/current/userguide/composite_builds.html)
- [Gradle: Isolated Projects](https://docs.gradle.org/current/userguide/isolated_projects.html)
