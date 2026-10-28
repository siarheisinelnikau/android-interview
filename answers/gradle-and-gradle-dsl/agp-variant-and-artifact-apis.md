# How do `finalizeDsl`, `beforeVariants`, `onVariants`, and artifact APIs replace `afterEvaluate` or hard-coded task names? What changes with AGP 9.0 public DSL types?

[Back to questions](../../README.md#gradle-and-gradle-dsl)

**Level:** Senior · **Topic:** Gradle and Gradle DSL · **Reviewed:** 2026-10-29

## Answer

Use the Android Components lifecycle at the point where the desired model is still mutable. `finalizeDsl` adjusts the DSL before AGP locks it. `beforeVariants` configures variant builders and can disable variants before their tasks are created. `onVariants` exposes variants and provider-backed properties after build-flow decisions are fixed.

Use public source and artifact APIs to register generated inputs or transform outputs. Wire task output providers into consumers; avoid guessed task names, direct edits to intermediates, and late `afterEvaluate` mutations of decisions AGP has already made.

AGP 9.0 enables `android.newDsl=true` by default. In that mode, casts to `BaseExtension` and legacy APIs such as `applicationVariants` are unavailable. This is not unconditional removal from every AGP 9 build: `android.newDsl=false` temporarily restores the deprecated implementation. AGP 9.4 also supports module-level opt-outs such as `android.newDsl.optOut=:legacy-lib`. The documentation schedules removal of this migration escape hatch for AGP 10; do not treat it as a permanent API.

Check supported callbacks/artifacts in the exact AGP version and test custom plugins across their claimed compatibility matrix.

## References

- [Android: extending AGP and its lifecycle](https://developer.android.com/build/extend-agp)
- [Android: AGP 9.0 public DSL migration](https://developer.android.com/build/releases/agp-9-0-0-release-notes)
- [Android: AGP 9.4 module-level opt-out](https://developer.android.com/build/releases/agp-9-4-0-release-notes)
