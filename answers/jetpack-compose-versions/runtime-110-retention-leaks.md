# Runtime 1.10 - why can retaining an Activity, View, or a key referencing them leak resources? What does `@DoNotRetain` communicate?

[Back to questions](../../README.md#jetpack-compose-versions)

**Level:** Senior · **Topic:** Jetpack Compose Versions · **Reviewed:** 2026-10-28

## Answer

Retaining a value can preserve everything it strongly references across configuration recreation. Retaining an old Activity or a View therefore keeps obsolete UI resources alive. The same applies when a retained key or captured lambda indirectly references them.

`@DoNotRetain` communicates that a type should not be retained; it is a tooling contract, not an automatic cleanup mechanism. Use an appropriate long-lived context only where the resource supports it, and define resource disposal explicitly.

Inspect both the retained value and its keys in a heap reference path. If a cache really belongs only to the current View, use a shorter owner rather than suppressing the warning. Retention across rotation never implies safety for all objects reachable from that value.

## References

- [Android: retain ownership restrictions](https://developer.android.com/develop/ui/compose/state-lifespans)
