# What causes an ANR? How would you use traces, StrictMode, and production reports to find the cause?

[Back to questions](../../README.md#performance-and-debugging)

**Level:** Middle · **Topic:** Performance and Debugging

## Answer

An ANR means the app failed a platform responsiveness requirement, such as processing input or completing a component callback within its allowed window. Different ANR types have different conditions and timeouts; not every ANR is simply one expensive draw call.

Read the production ANR type, main-thread stack, other thread stacks, and traces around the failure. Look for blocking I/O, lock contention, synchronous Binder calls, long computations, and resource starvation. The main thread can be waiting on a worker whose own stack reveals the actual cause.

Use StrictMode during development to catch relevant accidental disk/network work, and Perfetto or profiler traces to understand timing. Correlate with device and OS versions. Fix the blocking dependency or ownership problem rather than adding another thread without examining where the UI still waits for it.

## References

- [Android: ANR diagnosis](https://developer.android.com/topic/performance/vitals/anr)
