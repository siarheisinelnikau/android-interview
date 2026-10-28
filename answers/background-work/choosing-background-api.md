# When would you choose a coroutine, WorkManager, a foreground service, or `AlarmManager`?

[Back to questions](../../README.md#background-work)

**Level:** Middle · **Topic:** Background Work

## Answer

Choose an owner and execution contract before choosing an API. A coroutine is appropriate for work whose lifetime is owned by a screen, ViewModel, or other in-process scope. It does not survive process death.

WorkManager persists eligible deferrable work with constraints and retry support. A foreground service supports qualifying ongoing user-visible work, with service types, permissions, notifications, and start restrictions. AlarmManager schedules time-based triggers; exact alarms are reserved for eligible time-critical features.

A large user-initiated transfer may have a more suitable dedicated platform API. None of these choices grants unlimited execution or bypasses force-stop. Consider whether the work can be deferred, must resume after termination, has a real deadline, and can safely run more than once.

## References

- [Android: choosing background work](https://developer.android.com/develop/background-work/background-tasks)
