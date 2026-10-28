# Dependency locking vs. dependency verification - what does each protect, and what else is needed for reproducible builds?

[Back to questions](../../README.md#gradle-and-gradle-dsl)

**Level:** Senior · **Topic:** Gradle and Gradle DSL · **Reviewed:** 2026-10-29

## Answer

Dependency locking records selected versions for the configurations where it is enabled. It makes graph changes deliberate, including when a declared request is dynamic. Verification checks expected artifact/metadata checksums or signatures, helping detect changed or untrusted downloaded content.

Neither is a substitute for the other: the same version can serve different bytes, and authentic bytes can still belong to an unintended selected version. Review lock and verification-metadata updates; blindly regenerating expected checksums from an untrusted resolution only approves what was just downloaded.

Pin the Wrapper and toolchain inputs, control repositories and plugin resolution, and eliminate undeclared task inputs. A version catalog alone does not provide these guarantees. Define whether you need repeatable dependency selection or byte-identical final artifacts; timestamps, packaging, signing, and external services can still affect artifact reproducibility. Shared build-cache write access also needs an intentional trust boundary.

## References

- [Gradle: dependency locking](https://docs.gradle.org/current/userguide/dependency_locking.html)
- [Gradle: dependency verification](https://docs.gradle.org/current/userguide/dependency_verification.html)
