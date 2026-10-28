# Build types, product flavors, and source sets - how would you configure separate app variants?

[Back to questions](../../README.md#build-and-delivery)

**Level:** Middle · **Topic:** Build and Delivery

## Answer

Build types describe build/deployment characteristics such as debug versus release. Product flavors describe product or environment dimensions, such as a market or edition. A build variant combines a build type with the selected flavor in each dimension.

Source sets supply variant-specific code, resources, manifests, and dependencies according to the supported merge rules. Use configuration values for small differences and source-set implementations when behavior really differs; avoid duplicating entire applications for one endpoint change.

Keep the matrix intentional because every added dimension can multiply variants and CI cost. Use distinct application IDs when side-by-side installation is needed, protect signing configuration, and verify that a release variant cannot accidentally point at a development service. Endpoint configuration embedded in a build is not a secret-storage mechanism.

## References

- [Android: build variants and source sets](https://developer.android.com/build/build-variants)
