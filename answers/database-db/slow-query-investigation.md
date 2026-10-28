# How would you investigate a slow SQLite query? Discuss `EXPLAIN QUERY PLAN`, indexes, and pagination.

[Back to questions](../../README.md#database-db)

**Level:** Senior · **Topic:** Database (DB)

## Answer

Capture the exact SQL, bound-value characteristics, table sizes, and elapsed time. `EXPLAIN QUERY PLAN` helps identify full scans, index searches, covering indexes, and temporary sorting. Its output is a diagnostic format, not a stable production parsing API.

Check whether indexes match filtering and ordering, whether unnecessary columns or relationships are fetched, and whether an apparently cheap query is executed hundreds of times. Measure with realistic data distributions.

Large `OFFSET` pagination repeatedly skips earlier rows. For a stable ordered dataset, keyset pagination can continue after the previous `(created_at, id)` pair using a matching index. Include a unique tie-breaker and define behavior when rows change between pages. Indexes cannot compensate for an incorrect pagination contract.

## References

- [SQLite: EXPLAIN QUERY PLAN](https://sqlite.org/eqp.html)
- [SQLite: row-value pagination](https://sqlite.org/rowvalue.html)
