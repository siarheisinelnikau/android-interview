# How does Navigation 3's app-owned back stack differ from the `NavController` approach? How would you support predictive back and multiple panes?

[Back to questions](../../README.md#navigation)

**Level:** Senior · **Topic:** Navigation

## Answer

Navigation 3 observes an application-owned back stack of destination keys; navigation mutates that state explicitly. NavController owns its navigation state and exposes operations over a configured graph. Both still require deliberate state ownership and restoration.

NavDisplay renders entries and supports transitions and predictive-back integration. Scenes can present several entries together for adaptive multi-pane layouts. Entry decorators can supply saveable state and ViewModel stores; install the required owners instead of assuming Activity-wide defaults are destination-specific.

Keep keys small and serializable when restoration is required. Define what a pop means in single-pane and multi-pane arrangements, and test cancelled predictive gestures, external links, and resizing. Owning a list makes the state explicit but also makes the app responsible for valid stack operations and restoration policy.

## References

- [Android: Navigation 3 overview](https://developer.android.com/guide/navigation/navigation-3)
- [Android: Navigation 3 state preservation](https://developer.android.com/guide/navigation/navigation-3/save-state)
