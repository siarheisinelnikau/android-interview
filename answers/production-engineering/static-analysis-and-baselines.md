# How would you introduce lint or custom static-analysis rules without allowing an existing baseline to hide new violations?

[Back to questions](../../README.md#production-engineering)

**Level:** Middle · **Topic:** Production Engineering · **Reviewed:** 2026-10-29

## Answer

Choose analysis according to the contract being enforced. Android Lint understands Android resources, manifests, SDK use, and source patterns; other analyzers can enforce Kotlin-specific or repository-specific rules. Formatting, semantic correctness, and architecture policy are different goals.

Use a baseline to record intentionally deferred existing findings while failing relevant new violations. Review baseline updates as code changes: regenerating it on every CI run can silently approve newly introduced problems. Give suppressions a narrow scope and an explanation, and remove entries as defects are fixed.

For a custom rule, write positive and negative fixtures, test supported syntax/API levels, and evaluate false positives and runtime cost. Publish shared checks through maintained build conventions rather than copying divergent configuration into every module. Keep a small set of useful enforced rules before expanding coverage; a noisy report ignored by the team provides little protection.

## References

- [Android: lint configuration and baselines](https://developer.android.com/studio/write/lint)
- [Android: lint rule authoring](https://googlesamples.github.io/android-custom-lint-rules/)
