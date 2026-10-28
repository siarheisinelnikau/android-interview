# Runtime 1.11 - what does the experimental `SlotTable` rewrite aim to improve? How would you benchmark an opt-in runtime change?

[Back to questions](../../README.md#jetpack-compose-versions)

**Level:** Senior · **Topic:** Jetpack Compose Versions · **Reviewed:** 2026-10-28

## Answer

The experimental Runtime 1.11 SlotTable rewrite changes the internal representation used to track composition structure and remembered values, aiming to reduce copying and improve recomposition work such as reordering. It is an implementation optimization, not a new application state model.

Treat the opt-in as an app-wide runtime experiment. Compare representative startup, scrolling, reordering, and navigation workloads using a release-like build, with the same device conditions and repeated measurements. Verify saved state, effects, and correctness as well as frame timing.

Follow the exact release's feature-flag and R8 guidance; minification can affect assumed flag values. Do not reflect on internal table structures or assume that a benchmark improvement for a synthetic reorder guarantees an improvement for the whole product.

## References

- [Android: Compose Runtime 1.11 release notes](https://developer.android.com/jetpack/androidx/releases/compose-runtime)
