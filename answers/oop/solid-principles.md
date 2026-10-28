# Explain SOLID principles with examples.

[Back to questions](../../README.md#oop)

**Level:** Junior · **Topic:** OOP

## Answer

SOLID describes five design principles:

- **Single Responsibility:** group behavior that changes for the same reason. Formatting a receipt and charging a card need not share a class.
- **Open/Closed:** add a new payment strategy without repeatedly editing a central conditional.
- **Liskov Substitution:** a subtype must preserve the promises of its base type, including error behavior and preconditions.
- **Interface Segregation:** a receipt printer should not implement unrelated refund operations.
- **Dependency Inversion:** business policy depends on a gateway interface; the network implementation supplies that interface.

These are design tools, not a requirement to introduce an interface for every class. Evaluate whether an abstraction isolates a real source of change and makes the system easier to understand.

## References

- [Robert C. Martin: SOLID relevance](https://blog.cleancoder.com/uncle-bob/2020/10/18/Solid-Relevance.html)
