# How do Doze, App Standby, job quotas, and process death affect background work? How would you make work safe to retry?

[Back to questions](../../README.md#background-work)

**Level:** Senior · **Topic:** Background Work

## Answer

Doze defers background activity while a device is idle, and App Standby limits resources based on application usage. Job quotas and constraints can postpone or stop scheduled work. Process death can interrupt an operation after the server has acted but before the client records success.

Treat scheduling as eventual eligibility rather than a continuous execution guarantee. Persist the operation and progress, make server writes idempotent, and distinguish transient failures from permanent ones. Resume from checkpoints instead of restarting a large transfer blindly.

Use supported testing tools to force idle and standby conditions, and capture stop reasons and retry history. Foreground visibility, charging, or a wake lock should not be assumed to remove every quota or restriction. Respect explicit user force-stop rather than trying to relaunch around it.

## References

- [Android: Doze and App Standby](https://developer.android.com/training/monitoring-device-state/doze-standby)
- [Android: background resource limits](https://developer.android.com/topic/performance/power/power-details)
