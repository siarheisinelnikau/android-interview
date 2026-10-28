# Class naming - when do names like "Helper" and "Manager" hide unclear responsibilities?

[Back to questions](../../README.md#oop)

**Level:** Middle · **Topic:** OOP

## Answer

A name should communicate the responsibility and vocabulary of the domain. `Manager` and `Helper` are not inherently invalid, but names such as `UserManager` often conceal a mixture of authentication, persistence, validation, and presentation.

Ask what the object does and why it changes. `SessionStore`, `UserAuthenticator`, and `AvatarLoader` describe narrower contracts and help callers find the right dependency. If a class cannot be named clearly, inspect its responsibilities before renaming it.

Do not split a cohesive class only to avoid a word. Established framework names such as `WorkManager` are recognizable API names; the goal is understandable responsibilities, not a blacklist of suffixes.

## References

- [Kotlin: coding conventions and naming](https://kotlinlang.org/docs/coding-conventions.html)
- [Android: separation of concerns](https://developer.android.com/topic/architecture)
