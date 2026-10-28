# How do repository order, centralized repositories, and content filters affect dependency resolution and provenance?

[Back to questions](../../README.md#gradle-and-gradle-dsl)

**Level:** Middle · **Topic:** Gradle and Gradle DSL · **Reviewed:** 2026-10-29

## Answer

A repository supplies metadata and artifacts; it is not just a list of interchangeable download mirrors. Ordering, metadata availability, and repository-content rules influence where Gradle resolves a module and its artifacts. Once metadata is selected from a repository, do not assume missing artifacts will be freely mixed with another repository's module.

Centralize project repository declarations in settings where appropriate, and use repository-mode policy to prevent unnoticed per-project additions. Restrict private groups to their intended repository with suitable content or exclusive-content rules instead of searching public and private repositories indiscriminately.

Plugin repositories are configured separately through plugin management, and included builds can have independent settings. Avoid treating mavenLocal or flatDir as a reproducible production repository. Review credentials through appropriate external configuration, and inspect the actual origin when a checksum or dependency unexpectedly changes. Repository allowlists complement dependency verification; they do not replace it.

## References

- [Gradle: centralized repositories](https://docs.gradle.org/current/userguide/centralizing_repositories.html)
- [Gradle: repository content filtering](https://docs.gradle.org/current/userguide/filtering_repository_content.html)
- [Gradle: repository behavior](https://docs.gradle.org/current/userguide/declaring_repositories.html)
