# SOLID Principles

The SOLID principles are a set of design principles in object-oriented programming that aim to make software designs more understandable, flexible, and maintainable. These principles were introduced by Robert C. Martin (Uncle Bob).

## 1. Single Responsibility Principle (SRP)
A class should have only one reason to change, meaning it should have one responsibility or job. This makes the class easier to maintain and understand.

## 2. Open/Closed Principle (OCP)
Software entities should be open for extension but closed for modification. This allows new functionality to be added without altering existing code.

  The Open-Closed Principle requires that classes should be open for extension and closed for modification.

Modification means changing the code of an existing class, and extension means adding new functionality.

So this principle says, we should be able to add new functionality without touching the existing code. This is because whenever we will modify the existing code, there will be a chance to introduce a new bug. We should avoid touching the production code.

## 3. Liskov Substitution Principle (LSP)
Subtypes must be substitutable for their base types without altering the correctness of the program. This ensures that derived classes extend the base class without changing its behavior.

## 4. Interface Segregation Principle (ISP)
Clients should not be forced to depend on interfaces they do not use. Split interfaces into smaller, more specific ones to prevent unnecessary dependencies.

## 5. Dependency Inversion Principle (DIP)
High-level modules should not depend on low-level modules; both should depend on abstractions. Abstractions should not depend on details, keeping the system flexible and decoupled.
