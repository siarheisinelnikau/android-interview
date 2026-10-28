# How would you use previews and preview parameters to check dark mode, large fonts, locales, and different screen sizes? What still needs a device test?

[Back to questions](../../README.md#jetpack-compose)

**Level:** Middle · **Topic:** Jetpack Compose

## Answer

Create previews around composables that accept plain state and callbacks, with sample loading, empty, populated, and error states. Preview parameters and multipreview annotations can cover locales, dark mode, font scale, and window sizes without duplicating every preview function.

Keep runtime-only dependencies behind the screen boundary rather than making every preview construct a real ViewModel, network client, or database. Previews are useful for visual feedback, but their execution environment has limitations and may not match real system services.

Use device tests for permissions, keyboard/IME behavior, lifecycle and process restoration, accessibility interaction, and system integration. Benchmark on representative hardware for performance. A preview that looks correct is evidence about that rendering scenario, not a guarantee that the full screen works in an installed release build.

## References

- [Android: Compose previews](https://developer.android.com/develop/ui/compose/tooling/previews)
