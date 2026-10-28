# SQL basics: `SELECT`, `WHERE`, `ORDER BY`, and `JOIN`.

[Back to questions](../../README.md#database-db)

**Level:** Junior · **Topic:** Database (DB)

## Answer

`SELECT` chooses expressions to return, `FROM` identifies the source, `WHERE` filters rows, and `ORDER BY` defines result ordering. Without an explicit order, row order is not guaranteed.

An inner join returns matching rows from both sides. A left join also preserves left-side rows without a match, filling right-side columns with `NULL`.

```sql
SELECT u.id, u.name, o.id AS order_id
FROM users AS u
LEFT JOIN orders AS o ON o.user_id = u.id
WHERE u.active = 1
ORDER BY u.id, o.id;
```

Putting a condition on `o` in `WHERE` can remove the null-extended rows and accidentally defeat the left join. Use bound parameters for user input rather than string-concatenating SQL.

## References

- [SQLite: SELECT and join processing](https://sqlite.org/lang_select.html)
