# What responsibilities belong to a `ViewModel`, repository, and data source? When does a use case add value?

[Back to questions](../../README.md#patterns-and-architecture)

**Level:** Middle · **Topic:** Patterns and Architecture

## Answer

A ViewModel prepares screen state, handles presentation-related actions, and owns screen-level asynchronous work. A repository exposes application data and coordinates data sources, caching, consistency, and business data rules. A data source talks to one underlying mechanism, such as a DAO or remote API.

A use case adds value when it encapsulates reusable or complex business orchestration. A class that merely forwards one call for every repository method can add indirection without useful policy.

Keep UI framework objects out of long-lived data dependencies. Return domain-appropriate results rather than forcing callers to understand HTTP or cursor details. Define ownership, error mapping, and cancellation at each boundary; a layer diagram alone does not prevent duplicate requests or contradictory sources of truth.

## References

- [Android: data layer](https://developer.android.com/topic/architecture/data-layer)
- [Android: domain layer](https://developer.android.com/topic/architecture/domain-layer)
