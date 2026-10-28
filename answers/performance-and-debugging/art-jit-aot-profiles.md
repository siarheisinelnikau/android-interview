# How do ART, JIT, AOT, and Baseline Profiles relate to startup and runtime performance?

[Back to questions](../../README.md#performance-and-debugging)

**Level:** Middle · **Topic:** Performance and Debugging

## Answer

ART executes Android application code using a combination of interpretation, JIT compilation, and ahead-of-time compilation according to platform and installation conditions. JIT adapts to runtime behavior; AOT can compile known important code before it becomes a first-use cost.

Baseline Profiles identify representative important code paths so ART can optimize them, improving startup or interaction performance when installation and runtime support apply. They do not remove expensive I/O or fix an inefficient algorithm. Startup Profiles are related but serve a different purpose: helping optimize DEX layout for startup paths.

Generate profiles from realistic critical journeys and verify that they are packaged and applied. Measure the same release-like app with controlled compilation conditions. Avoid promising one universal speedup across all devices, OS versions, and workloads.

## References

- [Android: Baseline Profiles](https://developer.android.com/topic/performance/baselineprofiles/overview)
- [Android: Startup Profiles](https://developer.android.com/topic/performance/baselineprofiles/dex-layout-optimizations)
