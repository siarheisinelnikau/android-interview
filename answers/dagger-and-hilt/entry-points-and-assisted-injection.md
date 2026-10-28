# When do you need `@EntryPoint` or assisted injection? How would you avoid retaining a short-lived dependency in a longer-lived scope?

[Back to questions](../../README.md#dagger-and-hilt)

**Level:** Senior · **Topic:** Dagger and Hilt

## Answer

Use `@EntryPoint` to expose a small contract from a Hilt component to code Hilt cannot inject through its normal Android entry-point mechanism, such as a particular library boundary. Retrieve it from the correct component owner; it is not a reason to make every class query the container.

Assisted injection combines graph-supplied collaborators with values available only when an instance is created. An assisted factory accepts those runtime values. For assisted ViewModels, use Hilt's supported factory integration and remember that arbitrary runtime values are not automatically saved for process restoration.

Lifetime rules still apply: neither an entry point nor a factory makes an Activity safe to retain in a singleton. Pass a stable ID or a short-lived callback to the appropriate owner instead.

## References

- [Hilt: entry points](https://dagger.dev/hilt/entry-points.html)
- [Hilt: assisted ViewModel injection](https://dagger.dev/hilt/view-model.html)
