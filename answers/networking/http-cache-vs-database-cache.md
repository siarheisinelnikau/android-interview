# HTTP caching vs. a local database cache. How do you handle stale data, pagination, and offline errors?

[Back to questions](../../README.md#networking)

**Level:** Middle · **Topic:** Networking

## Answer

An HTTP cache stores response representations according to protocol headers, validators, freshness, and revalidation rules. It can reuse an ETag-backed response without the application implementing a complete data model.

A database cache stores application data for queries, relations, offline editing, and a defined source-of-truth policy. It needs explicit freshness, synchronization, invalidation, and pagination rules. A local row's existence does not prove it is current.

The two can coexist, but define which layer owns correctness. Avoid showing data from the wrong account after logout, overwriting pending offline edits with a stale response, or merging pages with incompatible query keys. Surface stale cached content and refresh failure separately when that improves the user experience. Respect server cache directives instead of treating every response as permanently reusable.

## References

- [RFC 9111: HTTP caching](https://www.rfc-editor.org/rfc/rfc9111)
- [Android: offline-first data layer](https://developer.android.com/topic/architecture/data-layer/offline-first)
