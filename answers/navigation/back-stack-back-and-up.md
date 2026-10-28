# What is a back stack? How do Back and Up navigation differ?

[Back to questions](../../README.md#navigation)

**Level:** Junior · **Topic:** Navigation

## Answer

A back stack records the navigation history to return through. Back normally reverses the user's navigation sequence and can leave the app or task. Up expresses the app's structural parent relationship, which can differ from the previous destination reached through an external deep link.

For example, opening a detail screen from another app should not necessarily fabricate the same history as opening it from the app's list. Define the expected Back and Up behavior for each entry flow.

Use the navigation owner's APIs and platform back integration rather than manually finishing random activities. Test nested graphs, dialogs, root destinations, external entry, and process restoration. Predictive back adds progress and cancellation to the interaction; commit stack mutation at the appropriate point.

## References

- [Android: navigation principles](https://developer.android.com/guide/navigation/principles)
