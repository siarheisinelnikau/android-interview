# WorkManager constraints, unique work, retries, and backoff - how would you implement reliable synchronization?

[Back to questions](../../README.md#background-work)

**Level:** Middle · **Topic:** Background Work

## Answer

Describe the sync with appropriate constraints, such as connectivity, then enqueue uniquely named work to avoid accidental duplicate schedules. Choose KEEP, REPLACE, or an append policy according to whether new input should preserve, replace, or follow existing work.

Return success for completed work, failure for a permanent error, and retry for a genuinely transient condition. Configure backoff and avoid retrying invalid credentials or malformed input indefinitely. Constraints can become unmet during execution, so cancellation and restart are normal.

Persist checkpoints and use stable operation IDs or server idempotency keys. Unique scheduling prevents some local duplicates but does not provide exactly-once side effects after a network timeout or process crash. Observe WorkInfo and record stop reasons to distinguish scheduling problems from application errors.

## References

- [Android: define WorkManager requests](https://developer.android.com/develop/background-work/background-tasks/persistent/getting-started/define-work)
- [Android: manage unique work](https://developer.android.com/develop/background-work/background-tasks/persistent/how-to/manage-work)
