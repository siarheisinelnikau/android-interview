# What does Room provide over working directly with SQLite?

[Back to questions](../../README.md#room-and-datastore)

**Level:** Junior · **Topic:** Room and DataStore

## Answer

Room maps entities and DAO declarations to SQLite operations and checks many SQL/schema mistakes at compile time. It provides generated access code, transactions, migration support, asynchronous queries, and observable query integrations, reducing repetitive cursor and mapping code.

It is still SQLite: you must understand indexes, constraints, query plans, and transaction boundaries. Room does not automatically make an inefficient join fast or invent a correct migration. Keep the database object appropriately scoped instead of creating one for every request.

A typical app defines an entity, a DAO interface, and a database class, then exposes domain-facing operations through a repository. Avoid leaking database rows into every UI contract when that would tightly couple presentation to storage details.

## References

- [Android: Room overview](https://developer.android.com/training/data-storage/room)
