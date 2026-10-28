# How would you investigate a memory leak, excessive allocations, or an out-of-memory crash using a heap dump?

[Back to questions](../../README.md#performance-and-debugging)

**Level:** Middle · **Topic:** Performance and Debugging

## Answer

A leak is unwanted retention; an out-of-memory failure can also result from legitimate but excessive live data or temporary allocation spikes. Start by measuring process memory and reproducing the operation repeatedly, then compare heap snapshots and allocation behavior.

Find retained Activities, Views, bitmaps, listeners, and caches, and inspect paths to GC roots rather than only large shallow object counts. A small singleton can retain a large graph. Remove the incorrect owner or registration; forcing GC cannot collect strongly reachable objects.

Inspect image decoding dimensions, cache limits, and duplicate buffers. Native and graphics allocations may not be fully explained by a managed heap dump, so use the appropriate native/process tools too. Verify that memory returns to a reasonable baseline after repeated navigation and resource cleanup.

## References

- [Android: memory profiler and heap dumps](https://developer.android.com/studio/profile/memory-profiler)
