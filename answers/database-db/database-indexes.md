# How do indexes speed up reads? What are the costs for writes and storage?

[Back to questions](../../README.md#database-db)

**Level:** Middle · **Topic:** Database (DB)

## Answer

An index stores a searchable ordering of indexed values and row references. It can avoid scanning every row and may also satisfy ordering or cover a query without reading the underlying table.

```sql
CREATE INDEX orders_customer_created
ON orders(customer_id, created_at);
```

This can help queries filtering by customer and ordering or ranging by creation time. Column order and selectivity matter; one large composite index does not optimize every combination of predicates.

Every write may need to update indexes, and each index consumes storage and cache space. Expressions and collation can affect whether an index is usable. Inspect the actual query plan with realistic data before adding indexes, and remove redundant ones rather than indexing every column.

## References

- [SQLite: query planning and indexes](https://sqlite.org/queryplanner.html)
