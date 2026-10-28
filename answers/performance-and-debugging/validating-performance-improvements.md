# How would you verify that an optimization improves user-visible performance across device classes and does not regress battery usage?

[Back to questions](../../README.md#performance-and-debugging)

**Level:** Senior · **Topic:** Performance and Debugging

## Answer

Define a user-visible metric and a representative journey before optimizing. Establish a baseline with repeated runs and fixed inputs, then compare latency distributions, frame timing, memory, and other relevant resources after the change.

Include slower devices and relevant Android versions; moving work from the main thread to a constantly active background loop can improve a local frame benchmark while worsening power use. Check retries, wakeups, network volume, and background duration alongside foreground responsiveness.

Use traces to explain the improvement and automated performance checks where stable enough. Roll out with production monitoring and guard against regressions in crashes, ANRs, battery behavior, and task success. An optimization is successful when its practical benefit exceeds its cost without violating correctness or another important resource constraint.

## References

- [Android: measure performance](https://developer.android.com/topic/performance/measuring-performance)
- [Android: power optimization](https://developer.android.com/topic/performance/power)
