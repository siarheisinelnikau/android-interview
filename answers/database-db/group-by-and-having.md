# Difference between `WHERE` and `HAVING`. How do `GROUP BY` and aggregate functions work?

[Back to questions](../../README.md#database-db)

**Level:** Middle · **Topic:** Database (DB)

## Answer

`WHERE` filters input rows before grouping. `GROUP BY` collects rows into groups, aggregate functions compute results such as `COUNT` or `SUM`, and `HAVING` filters the resulting groups.

```sql
SELECT customer_id, COUNT(*) AS order_count
FROM orders
WHERE status = 'paid'
GROUP BY customer_id
HAVING COUNT(*) >= 3
ORDER BY order_count DESC, customer_id;
```

This returns customers with at least three paid orders, not customers with at least three orders of any status. `COUNT(*)` counts rows; `COUNT(column)` excludes null values. Select grouping keys or well-defined aggregates instead of depending on SQLite's permissive handling of unrelated bare columns. Add a deterministic tie-breaker when paginating grouped results.

## References

- [SQLite: aggregate queries](https://sqlite.org/lang_select.html)
