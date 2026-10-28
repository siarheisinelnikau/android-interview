# How would you design feature flags and remote configuration with safe defaults, offline behavior, and a useful kill switch?

[Back to questions](../../README.md#production-engineering)

**Level:** Middle · **Topic:** Production Engineering · **Reviewed:** 2026-10-29

## Answer

Ship explicit local defaults so the app can operate before a successful fetch and while offline. Define how cached values expire, how fetch and activation differ, and when a new configuration may affect an already running user journey. Avoid changing several related flags independently if their combination can create an invalid state.

Assign stable rollout/experiment membership where required and record the relevant configuration version for diagnosis. A kill switch must be checked before starting the work it controls, with a clear local fallback. It cannot instantly reach an offline device or fix a startup crash that prevents configuration handling.

Remote configuration is client-readable, so keep secrets and authorization decisions on the server. Test missing, malformed, stale, and incompatible values, and define cleanup ownership when a flag changes during a screen or background task. Remove obsolete flags after rollout so permanent branching does not become hidden product complexity.

## References

- [Firebase: remote configuration loading strategies](https://firebase.google.com/docs/remote-config/loading)
