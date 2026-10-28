# Compare `ArrayList` and `LinkedList`. How do access patterns and memory overhead affect the choice?

[Back to questions](../../README.md#collections)

**Level:** Middle · **Topic:** Collections

## Answer

`ArrayList` stores references in an array, providing O(1) indexed access and amortized O(1) append. Inserting or removing near the beginning shifts elements. Its compact storage usually provides good locality.

`LinkedList` allocates nodes with links. Indexed access walks nodes and is O(n); inserting at an already located iterator position is O(1), but finding that position may be O(n). Node allocation, pointer chasing, and GC overhead often outweigh the apparent insertion advantage.

For most Android UI data, start with an array-backed list. For queue operations at both ends, consider `ArrayDeque` rather than assuming a linked list is faster. Measure representative workloads before changing the structure.

## References

- [Java: LinkedList](https://docs.oracle.com/en/java/javase/25/docs/api/java.base/java/util/LinkedList.html)
- [Java: ArrayDeque](https://docs.oracle.com/en/java/javase/25/docs/api/java.base/java/util/ArrayDeque.html)
