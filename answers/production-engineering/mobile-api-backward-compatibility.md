# How do you evolve a backend API while old app versions remain installed? Which seemingly additive changes can break a mobile client?

[Back to questions](../../README.md#production-engineering)

**Level:** Senior · **Topic:** Production Engineering · **Reviewed:** 2026-10-29

## Answer

Treat the API as a contract used by independently deployed clients. Preserve existing field meanings, authentication flows, and request semantics while introducing new behavior through compatible additions, explicit versions, or negotiated capabilities. Do not assume all devices update when the backend is deployed.

An added response field can break a strict parser; a new enum value can break exhaustive decoding; an optional request field can become a breaking change if the server suddenly requires it. Changing nullability, identifier formats, error semantics, or pagination ordering can also violate client assumptions without changing the endpoint URL.

Test representative old/new client contracts against backend changes, include unknown-field/enum and missing-data cases, and monitor usage before removing support. Tolerant parsing should not silently turn an unknown payment state into success. Use a deliberate minimum-supported-version policy when compatibility cannot be preserved, and keep durable local data migration separate from wire-format evolution.

## References

- [Google API guidance: backward compatibility](https://google.aip.dev/180)
- [Kotlin serialization: JSON configuration](https://kotlinlang.org/docs/serialization.html)
