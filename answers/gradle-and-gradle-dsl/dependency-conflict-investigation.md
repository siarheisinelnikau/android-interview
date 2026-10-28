# How would you diagnose an unexpected transitive dependency version? When are constraints or exclusions safer than forcing a version?

[Back to questions](../../README.md#gradle-and-gradle-dsl)

**Level:** Middle · **Topic:** Gradle and Gradle DSL · **Reviewed:** 2026-10-29

## Answer

Inspect the exact consumer configuration, because debug/release and compile/runtime graphs can differ. A dependencies report shows the graph; dependencyInsight explains selection paths and reasons for a particular module.

```text
./gradlew :app:dependencyInsight --configuration debugRuntimeClasspath --dependency example-library
```

Use `gradlew.bat` on Windows, and substitute the actual module/configuration. Determine whether a platform, strict constraint, conflict rule, direct dependency, or substitution caused the selection.

Prefer upgrading compatible libraries or expressing a justified constraint over forcing an arbitrary version across the entire build. Excluding a transitive dependency is safe only when the remaining graph still supplies the contract that the library needs, or the feature using it is genuinely absent. Compilation alone may not detect a missing runtime class or incompatible method. Avoid duplicate JAR/AAR workarounds and blanket packaging exclusions that hide the dependency problem without making the code compatible.

## References

- [Gradle: dependency reports and insight](https://docs.gradle.org/current/userguide/viewing_debugging_dependencies.html)
- [Gradle: dependency constraints](https://docs.gradle.org/current/userguide/dependency_constraints.html)
