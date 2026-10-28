# Worst-case vs. amortized complexity - how does this apply to a growing array or a hash table?

[Back to questions](../../README.md#algorithms)

**Level:** Senior · **Topic:** Algorithms

## Answer

Worst-case complexity bounds one operation under its most expensive valid input. Amortized complexity spreads occasional expensive operations across a sequence; it does not depend on random input.

Appending to a growing array is usually cheap, but a resize allocates storage and copies existing elements: that particular append is O(n). With geometric growth, n appends perform O(n) total work, giving amortized O(1) per append. An insertion near the front still shifts elements and is O(n).

Hash tables likewise pay occasional resize costs; their usual constant-time operations additionally assume suitable hash distribution. Amortized throughput does not guarantee low tail latency: a single resize can still be noticeable in a frame-critical path.

## References

- [Java: ArrayList complexity](https://docs.oracle.com/en/java/javase/25/docs/api/java.base/java/util/ArrayList.html)
