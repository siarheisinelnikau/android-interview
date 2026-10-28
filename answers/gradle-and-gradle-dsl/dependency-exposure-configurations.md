# Compare `api`, `implementation`, `compileOnly`, and `runtimeOnly`. How does dependency exposure affect consumers and recompilation?

[Back to questions](../../README.md#gradle-and-gradle-dsl)

**Level:** Middle · **Topic:** Gradle and Gradle DSL · **Reviewed:** 2026-10-29

## Answer

In a library, api exposes a dependency on the consumer's compile classpath as well as the appropriate runtime path. implementation keeps the dependency out of the consumer's public compile contract, while still allowing it to be included transitively where runtime resolution requires it.

Use api when the library's public signatures genuinely expose that dependency's types. Use implementation for internal details; this reduces unnecessary compile coupling and can limit recompilation when an internal dependency changes. It is not a security mechanism and does not promise that dependency code is absent from an application package.

compileOnly makes a dependency available for compilation without automatically supplying it at runtime. runtimeOnly supplies runtime behavior without compiling against its types. The runtime must actually provide a compile-only contract if generated code uses it. Apply these concepts to the relevant plugin and variant rather than assuming every configuration exists in every project.

## References

- [Gradle: Java library API separation](https://docs.gradle.org/current/userguide/java_library_plugin.html)
- [Gradle: dependency configurations](https://docs.gradle.org/current/userguide/dependency_configurations.html)
