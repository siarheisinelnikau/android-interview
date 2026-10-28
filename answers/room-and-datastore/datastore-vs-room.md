# When would you choose Preferences DataStore, typed DataStore, or Room? How would you migrate from `SharedPreferences`?

[Back to questions](../../README.md#room-and-datastore)

**Level:** Middle · **Topic:** Room and DataStore

## Answer

Preferences DataStore stores key/value settings without a predefined schema. Typed DataStore persists a value using a chosen serializer, such as a structured settings model. Room fits relational data, partial updates, queries, relationships, and larger datasets.

DataStore exposes asynchronous reads through Flow and transactional read-modify-write updates. It is not a relational database and should not be used as a substitute for indexed queries over a large collection. Follow its instance and process ownership rules for a given file.

Migrate existing preferences with the provided SharedPreferences migration support, defining key mapping and defaults. Account for failures and idempotency; do not keep two independent writers treating old preferences and the new store as competing sources of truth.

## References

- [Android: DataStore](https://developer.android.com/topic/libraries/architecture/datastore)
