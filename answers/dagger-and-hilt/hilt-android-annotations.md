# How do `@HiltViewModel`, `@AndroidEntryPoint`, and `@InstallIn` work together?

[Back to questions](../../README.md#dagger-and-hilt)

**Level:** Middle · **Topic:** Dagger and Hilt

## Answer

`@HiltAndroidApp` sets up the application's Hilt container. `@AndroidEntryPoint` integrates supported Android components with their generated injection graph. `@HiltViewModel` marks a constructor-injected ViewModel for Hilt-aware creation through the ViewModel machinery.

`@InstallIn` places a module or entry-point declaration in the chosen Hilt component; it does not instantiate a class merely because the annotation exists. The component determines binding availability and supported scopes.

Obtain ViewModels through the appropriate owner-aware API, including the relevant Compose integration, rather than constructing them manually or injecting a ViewModel as an ordinary graph object. The selected ViewModelStore owner still controls lifetime. A composable itself normally does not need `@AndroidEntryPoint`; its hosting component provides the integration boundary.

## References

- [Android: Hilt integration](https://developer.android.com/training/dependency-injection/hilt-android)
- [Hilt: ViewModels](https://dagger.dev/hilt/view-model.html)
