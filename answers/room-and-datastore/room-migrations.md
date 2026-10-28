# Automatic vs. manual migrations. Why export schemas, and how do you test migration paths without losing user data?

[Back to questions](../../README.md#room-and-datastore)

**Level:** Middle · **Topic:** Room and DataStore

## Answer

An automatic migration uses exported old and new schemas to generate supported changes. Ambiguous changes such as renames may need an `AutoMigrationSpec`; complex transformations require a manual migration. A version bump by itself does not preserve data.

Keep schema history in version control. Test supported upgrade paths using `MigrationTestHelper`: create an old schema, insert representative old data, migrate, validate the resulting schema, and assert that data was transformed correctly. Include multi-version jumps that real users can take.

Destructive fallback recreates storage and loses data; use it only when that loss is an explicit product decision. Test new constraints, null defaults, renamed columns, and transaction failures, rather than checking only that the upgraded database opens.

## References

- [Android: Room migrations and testing](https://developer.android.com/training/data-storage/room/migrating-db-versions)
