# What do R8 shrinking, optimization, and obfuscation do? How do keep rules and mapping files help diagnose release-only failures?

[Back to questions](../../README.md#build-and-delivery)

**Level:** Middle · **Topic:** Build and Delivery

## Answer

R8 removes unused code, optimizes reachable code, and can rename identifiers. Resource shrinking removes unused resources through related build tooling. These changes can expose incorrect assumptions around reflection, generated names, serialization, or code reached only through external configuration.

Use narrow keep rules for genuine dynamic entry points and the library's supported consumer rules. Keeping the entire application can hide the problem and sacrifice optimization. Build and test the release variant rather than assuming debug behavior proves the optimized result is correct.

Archive the correct mapping file for each distributed version so production stack traces can be retraced. For a release-only crash, reproduce with matching optimization and rules, inspect missing/renamed dynamic members, and change the contract or targeted rule instead of disabling all optimization immediately.

## References

- [Android: enable R8 optimization](https://developer.android.com/topic/performance/app-optimization/enable-app-optimization)
- [Android: keep rules](https://developer.android.com/topic/performance/app-optimization/keep-rules-overview)
