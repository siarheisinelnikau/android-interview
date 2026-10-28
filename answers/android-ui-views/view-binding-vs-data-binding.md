# View Binding vs. Data Binding. How do you manage a Fragment's binding across its view lifecycle?

[Back to questions](../../README.md#android-ui-views)

**Level:** Middle · **Topic:** Android UI (Views)

## Answer

View Binding generates typed references for Views in a layout. Data Binding additionally supports layout expressions and binding observable values, with extra generated code and configuration. View Binding is a simpler choice when the layout only needs safe View access.

A Fragment's binding belongs to its View lifecycle:

```kotlin
private var _binding: ScreenBinding? = null
private val binding get() = checkNotNull(_binding)

override fun onDestroyView() {
    super.onDestroyView()
    _binding = null
}
```

Initialize it when inflating the View and ensure collectors or callbacks cannot use it after destruction. Clearing the field does not help if a long-lived lambda captured the old binding separately. Keep View-specific work owned by `viewLifecycleOwner`.

## References

- [Android: View Binding](https://developer.android.com/topic/libraries/view-binding)
- [Android: Data Binding](https://developer.android.com/topic/libraries/data-binding)
