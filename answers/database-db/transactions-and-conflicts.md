# Explain transactions, foreign keys, and conflict handling in SQLite.

[Back to questions](../../README.md#database-db)

**Level:** Middle · **Topic:** Database (DB)

## Answer

A transaction groups changes into a unit that commits or rolls back. Use it for invariants such as updating an account balance together with inserting its ledger record. Keep transactions short; SQLite permits multiple readers but serializes writers, with details depending on journal mode.

Foreign keys prevent invalid references and can define delete/update actions. In standalone SQLite, ensure enforcement is enabled for the connection; declaring a constraint alone is insufficient if checks are disabled.

Choose conflict handling deliberately. Ignoring a conflicting insert may hide missing work. SQLite `REPLACE` can delete a conflicting row and insert another, triggering consequences different from an update. Use an appropriate UPSERT when you mean update-on-conflict, and test constraints and rollback behavior.

## References

- [SQLite: transactions](https://sqlite.org/lang_transaction.html)
- [SQLite: foreign keys](https://sqlite.org/foreignkeys.html)
- [SQLite: conflict resolution](https://sqlite.org/lang_conflict.html)
