# How would you correlate crashes, ANRs, performance regressions, and failed user journeys with a release without logging sensitive data?

[Back to questions](../../README.md#production-engineering)

**Level:** Senior · **Topic:** Production Engineering · **Reviewed:** 2026-10-29

## Answer

Attach a stable release/build identity and a small set of useful diagnostic dimensions, such as OS, device class, non-sensitive operation state, and applicable feature/configuration version. Preserve deobfuscation mappings and native symbols for the exact distributed artifact.

Use structured events and bounded breadcrumbs to reconstruct relevant transitions without copying request bodies, access tokens, user-entered text, or entire objects into logs. A pseudonymous identifier can still carry privacy obligations; collect only what is necessary and define retention/access policy.

Compare rates using a clear denominator, such as affected users, sessions, or attempted operations. Raw crash counts can rise simply because traffic increased. Segment by rollout cohort and distinguish app version from a remotely changed flag or backend deployment. Observability should help answer which journey failed and why, not just whether a process terminated. Test the reporting pipeline with controlled events and verify symbolication before relying on it during an incident.

## References

- [Firebase: custom keys, logs, and crash diagnostics](https://firebase.google.com/docs/crashlytics/customize-crash-reports)
- [Android: Android vitals](https://developer.android.com/topic/performance/vitals)
