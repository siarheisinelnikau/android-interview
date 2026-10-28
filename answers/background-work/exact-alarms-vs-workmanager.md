# Why is WorkManager unsuitable for exact-time alarms? What restrictions apply to exact alarms?

[Back to questions](../../README.md#background-work)

**Level:** Middle · **Topic:** Background Work

## Answer

WorkManager runs when its scheduling conditions and system policy permit; an initial delay is a minimum delay, not an exact execution time. Periodic work is likewise inexact. It is appropriate for eventual work, not a user-set alarm clock.

AlarmManager provides time-based triggers, including exact APIs for eligible use cases. Recent Android versions restrict exact alarm access through special access or narrowly applicable permissions, depending on the target and use case. Check capability before scheduling and handle revocation.

Prefer an inexact alarm when a time window is acceptable. Keep alarm handling short and hand off eligible follow-up work appropriately. Exact alarms still have idle-mode limits, reboot considerations, and user-control rules; repeatedly scheduling them is not a general background execution strategy.

## References

- [Android: scheduling alarms and exact access](https://developer.android.com/develop/background-work/services/alarms)
