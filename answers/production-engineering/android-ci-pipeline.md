# What should an Android CI pipeline validate before producing a release? How would you separate fast feedback from device and release checks?

[Back to questions](../../README.md#production-engineering)

**Level:** Middle · **Topic:** Production Engineering · **Reviewed:** 2026-10-29

## Answer

Run fast deterministic checks early: compile relevant modules, execute local tests, and run appropriate lint/static analysis. Add instrumented and integration checks for platform behavior, with a deliberate device/API matrix rather than every possible combination on every small change.

Validate a release-like variant too, because shrinking, resources, manifest merging, signing configuration, and dependency differences can reveal failures hidden by debug builds. Pin the Wrapper/toolchain inputs and keep dependency/cache reuse controlled. Separate untrusted pull-request execution from jobs with signing or publishing credentials.

Promote an identified tested artifact through release stages instead of silently rebuilding different bytes for each environment. Archive reports, mapping files, native symbols when needed, and enough build metadata to diagnose the distributed version. A green unit-test task is useful evidence about a subset of behavior; it does not replace installed-artifact verification or a deliberate release decision.

## References

- [Android: continuous integration](https://developer.android.com/training/testing/continuous-integration)
- [Android: app signing](https://developer.android.com/studio/publish/app-signing)
