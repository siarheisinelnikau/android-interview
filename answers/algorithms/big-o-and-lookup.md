# What is Big O notation? Compare searching in a list and looking up a key in a hash map.

[Back to questions](../../README.md#algorithms)

**Level:** Junior · **Topic:** Algorithms

## Answer

Big O describes an asymptotic upper bound on resource growth as input size increases. It omits constant factors and is not a direct stopwatch prediction.

An unsorted list search is O(n) in the worst case because every element may need comparison. A well-distributed hash map normally offers expected O(1) lookup, with hashing and equality costs included in the real workload. Collisions and resizing prevent a universal constant-time guarantee. A sorted array permits O(log n) binary search but may require O(n) insertion.

Also discuss memory, cache locality, key cost, and data size. For ten entries, a linear search can be simpler and faster than allocating a map.

## References

- [Java: HashMap performance contract](https://docs.oracle.com/en/java/javase/25/docs/api/java.base/java/util/HashMap.html)
- [Java: Collections binarySearch](https://docs.oracle.com/en/java/javase/25/docs/api/java.base/java/util/Collections.html)
