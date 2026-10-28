# Extension functions and properties - how are they resolved, and can they override members?

[Back to questions](../../README.md#kotlin)

**Level:** Middle · **Topic:** Kotlin

## Answer

An extension provides callable syntax for a type without modifying that type or adding virtual members. Resolution is based primarily on the receiver's declared static type and the visible declarations at the call site.

```kotlin
open class Animal
class Cat : Animal()
fun Animal.label() = "animal"
fun Cat.label() = "cat"
val pet: Animal = Cat()
check(pet.label() == "animal")
```

A compatible real member takes precedence over an extension; an extension cannot override it. Extension properties do not gain ordinary backing fields, so they compute or delegate elsewhere.

Use extensions for cohesive operations on existing types, but avoid hiding expensive I/O behind property-like syntax or introducing ambiguous widely imported names. Nullable receiver extensions can be useful when their null behavior is explicit.

## References

- [Kotlin: extensions](https://kotlinlang.org/docs/extensions.html)
