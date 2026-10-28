# What do Dagger components and subcomponents represent? How does Hilt organize them for Android?

[Back to questions](../../README.md#dagger-and-hilt)

**Level:** Middle · **Topic:** Dagger and Hilt

## Answer

A Dagger component is an entry point into a dependency graph and an owner of scoped bindings. A subcomponent can access parent bindings and define a narrower graph and lifetime. This is graph composition, not ordinary implementation inheritance used merely for code reuse.

Hilt generates a standard hierarchy of components associated with Android lifetimes, reducing custom component wiring. Install a module in the component where its bindings are available and where their lifetime is valid.

A child can depend on an appropriate parent binding, but the parent cannot simply capture a child-scoped object. Do not put all dependencies in the application graph to make them easy to reach: doing so can retain screen objects and erase useful ownership boundaries.

## References

- [Dagger: subcomponents](https://dagger.dev/dev-guide/subcomponents.html)
- [Hilt: component hierarchy](https://dagger.dev/hilt/components.html)
