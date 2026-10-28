# Which context-parameter capabilities became stable in 2.4? Why do explicit context arguments still need experimental opt-in?

[Back to questions](../../README.md#kotlin-versions)

**Level:** Senior · **Topic:** Kotlin Versions · **Version:** Kotlin 2.4 · **Reviewed:** 2026-10-29

## Answer

Kotlin 2.4 stabilizes the core context-parameter feature, allowing named contextual dependencies without the old context-receivers design. The stabilization does not cover every related capability: explicit context arguments and certain callable-reference support remain experimental under the documented release rules.

Implicit resolution searches the surrounding context for suitable types and can be ambiguous when competing candidates are available. Explicit context arguments address some such call-site ambiguity, but in Kotlin 2.4 require `-Xexplicit-context-arguments`. Core context parameters do not need the former experimental context-parameter flag. Callable references involving context parameters remain experimental too; do not infer their status from the core feature.

During migration, remove obsolete context-receiver configuration and check compiler/plugin support. Separate using stable context parameters from enabling optional experimental syntax. Public APIs should make their contextual requirements understandable; hiding a large service graph in context can reduce the readability that named dependencies were meant to improve.

## References

- [Kotlin 2.4: stable and experimental context capabilities](https://kotlinlang.org/docs/whatsnew24.html)
- [Kotlin: context parameters](https://kotlinlang.org/docs/context-parameters.html)
