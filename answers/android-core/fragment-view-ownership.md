# How do a Fragment's lifecycle and its view lifecycle affect observers, coroutines, and references to Views?

[Back to questions](../../README.md#android-core)

**Level:** Middle · **Topic:** Android Core

## Answer

A Fragment's instance can remain alive while its View is destroyed, for example on the back stack. A coroutine in the Fragment's own scope can therefore outlive the binding it captured.

Bind UI observation to `viewLifecycleOwner`, use its lifecycle scope with `repeatOnLifecycle`, and clear binding references in `onDestroyView`. Attach and remove View-specific listeners within the same ownership boundary. Business state can live in a ViewModel so a replacement View can render it again.

Do not solve this by dropping every update when binding is null: that may merely hide the incorrect ownership. Recollect current state when the new View is started. For jobs that should survive the View, ensure they do not capture that View or its Activity accidentally.

## References

- [Android: Fragment view lifecycle](https://developer.android.com/guide/fragments/lifecycle)
