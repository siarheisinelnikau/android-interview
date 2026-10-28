# What does the Gradle Wrapper pin? How would you upgrade and verify the build distribution?

[Back to questions](../../README.md#gradle-and-gradle-dsl)

**Level:** Junior · **Topic:** Gradle and Gradle DSL · **Reviewed:** 2026-10-29

## Answer

The Wrapper scripts launch the Gradle distribution selected in `gradle-wrapper.properties`, downloading it when necessary. This lets developers and CI use the project-selected Gradle version instead of whichever installation happens to be on the machine.

Commit the scripts, properties, and Wrapper JAR. Use the supported Wrapper task to upgrade, review the resulting files and compatibility requirements, and configure distribution checksum verification through `distributionSha256Sum`. Validate changes to the executable Wrapper JAR as well; verifying the downloaded ZIP and verifying the bootstrap code are different checks.

The Wrapper does not pin the complete environment. JDK selection, Android SDK/NDK packages, plugins, repositories, and resolved dependencies still need intentional configuration. Run a representative build on CI after an upgrade instead of assuming that updating one URL preserves compatibility.

## References

- [Gradle: Wrapper configuration, upgrades, and verification](https://docs.gradle.org/current/userguide/gradle_wrapper.html)
