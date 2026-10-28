# Foreground service types, permissions, and background start restrictions - what must you account for?

[Back to questions](../../README.md#background-work)

**Level:** Middle · **Topic:** Background Work

## Answer

A foreground service must represent a qualifying user-visible operation, publish its required notification promptly, and declare the appropriate service type and permissions. Starting it from the background is restricted unless a documented exemption applies.

Different types can impose different prerequisites and time limits. A camera or location permission granted while the app is in use does not automatically permit starting resource access from the background. Calling `startForegroundService()` also does not remove the requirement to promote the service within the platform deadline.

Design a visible start/stop flow, clean up resources, and checkpoint work that can be interrupted. Test denied notification permission independently from service permissions and start eligibility. Use WorkManager or another purpose-specific API when the operation does not qualify for a foreground service.

## References

- [Android: foreground service overview](https://developer.android.com/develop/background-work/services/fgs)
- [Android: background-start restrictions](https://developer.android.com/develop/background-work/services/fgs/restrictions-bg-start)
