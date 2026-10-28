# How would you measure cold startup and scrolling performance with Macrobenchmark and Perfetto? Why use a release-like build?

[Back to questions](../../README.md#performance-and-debugging)

**Level:** Senior · **Topic:** Performance and Debugging

## Answer

Macrobenchmark measures whole-app operations such as startup and scrolling in a separate test process. Use a profileable, release-like target build; debug tooling, missing optimization, and different compilation modes can distort results.

For startup, distinguish time to initial display from time to fully drawn content and define what usable means for the feature. For scrolling, examine frame timing and outliers during a reproducible gesture and dataset. Perfetto traces help attribute delays to main-thread work, rendering, scheduling, I/O, or contention.

Repeat runs on representative physical devices with controlled thermal, battery, and compilation conditions. Compare distributions and trace evidence rather than one lucky run. Separate app cold-start conditions from unrelated network variability, and keep benchmark inputs realistic enough to reveal the production bottleneck.

## References

- [Android: Macrobenchmark](https://developer.android.com/topic/performance/benchmarking/macrobenchmark-overview)
- [Perfetto: trace analysis](https://perfetto.dev/docs/)
