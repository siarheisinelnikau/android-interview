# Compare `==` and `===`. How are `equals()` and `hashCode()` related?

[Back to questions](../../README.md#kotlin)

**Level:** Junior · **Topic:** Kotlin

## Answer

`==` performs structural equality through the applicable `equals` contract, with null-safe handling. `===` checks reference identity for object references. Two distinct data-class instances can therefore be equal without being the same instance.

If two objects are equal, they must have the same hash code. Unequal objects may share a hash code. Hash-based collections use both hashing and equality, so overriding one without the other breaks their contract.

```kotlin
data class UserId(val value: Long)
check(UserId(7) == UserId(7))
```

Keep equality consistent and avoid mutating equality-relevant fields while an object is used as a hash key. Arrays use identity-style equality by default; use appropriate content comparison functions when comparing their elements is the intended meaning.

## References

- [Kotlin: equality](https://kotlinlang.org/docs/equality.html)
