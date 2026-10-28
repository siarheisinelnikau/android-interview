# Generics - declaration-site variance (`in`/`out`), type projections, and star projections. How do they relate to Java wildcards?

[Back to questions](../../README.md#kotlin)

**Level:** Senior · **Topic:** Kotlin

## Answer

`out T` makes a type a producer: a `Producer<Cat>` can be used where `Producer<Animal>` is expected because reading a Cat as an Animal is safe. `in T` makes it a consumer: a consumer able to accept any Animal can also accept Cats. Invariant types allow neither substitution by default.

Use-site projections constrain operations on a particular reference. A star projection represents an unknown argument with safe operations determined by its declaration bounds; it is not a license to insert arbitrary values.

Java commonly expresses these ideas with `? extends` and `? super` wildcards. JVM generic arguments are usually erased at runtime, so casts may check only the outer type. Explain the permitted reads and writes, not only the producer/consumer mnemonic.

## References

- [Kotlin: generics, variance, and erasure](https://kotlinlang.org/docs/generics.html)
