# A function type vs. a `fun interface` - how do SAM conversion, identity, and Java interoperability affect the choice?

[Back to questions](../../README.md#kotlin)

**Level:** Middle · **Topic:** Kotlin

## Answer

A function type describes a callable signature, such as `(User) -> Boolean`, and is convenient for ordinary higher-order Kotlin APIs. A `fun interface` defines a named nominal contract with one abstract method and can also provide default behavior or domain-specific extension functions.

SAM conversion adapts a compatible lambda or callable reference to the functional interface. A type alias for a function type does not create the same distinct nominal type.

Choose a function type for a simple action or transformation, and a fun interface when a named reusable contract or Java-facing API adds value. Do not use lambda instance identity as a business identifier or assume a specific allocation strategy: compiler implementation and conversion sites can change how callable objects are represented.

## References

- [Kotlin: functional interfaces](https://kotlinlang.org/docs/fun-interfaces.html)
