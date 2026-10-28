# Visibility modifiers - what does `internal` mean, and how does it differ from Java package visibility?

[Back to questions](../../README.md#kotlin)

**Level:** Middle · **Topic:** Kotlin

## Answer

`public` is the default visibility, `private` restricts access to its declaration scope, and `protected` grants supported subclass access. A top-level private declaration is visible within its file. `internal` exposes a declaration within the same Kotlin compilation module, not within a Java package.

A Gradle project can compile several modules or source-set compilations; understand the actual boundary instead of equating a package name with a module. Tests can have friend-module access under supported tooling arrangements.

On the JVM, internal is primarily a Kotlin source-level API rule and can involve name mangling; it is not a security boundary against reflection or Java access. Keep sensitive data protected by actual application and platform controls, not only by a visibility modifier.

## References

- [Kotlin: visibility modifiers](https://kotlinlang.org/docs/visibility-modifiers.html)
