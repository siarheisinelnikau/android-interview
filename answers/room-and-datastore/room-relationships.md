# How do you model one-to-many and many-to-many relationships in Room? When is `@Transaction` needed?

[Back to questions](../../README.md#room-and-datastore)

**Level:** Middle · **Topic:** Room and DataStore

## Answer

For one-to-many data, store the parent's ID as a foreign key on each child. A Room result object can combine `@Embedded` parent data and a `@Relation` child list. Define actual foreign-key constraints and indexes separately; `@Relation` is a mapping instruction, not a database constraint.

For many-to-many relationships, use a junction entity containing both IDs, normally with a composite primary key. `@Junction` tells Room how to traverse that association.

Relation loading may execute several queries. Use `@Transaction` on the DAO operation when all results must describe one consistent database snapshot. Also use a transaction for a multi-step write invariant. A single SQL join is an alternative when you want explicit projections and query behavior.

## References

- [Android: Room relationships](https://developer.android.com/training/data-storage/room/relationships)
- [Android: many-to-many relationships](https://developer.android.com/training/data-storage/room/relationships/many-to-many)
