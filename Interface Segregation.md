# Interface Segregation Principle (ISP)

The Interface Segregation Principle (ISP) states that no client should be forced to depend on interfaces it does not use. Interfaces should be small and specific to the client's needs, rather than large and generalized.

## Bad Example

In this example, the `User` interface is too large and includes methods that are not needed by all classes.

### Code Example

```swift
// A large interface with all possible user actions
protocol User {
    func manageUsers()        // Admin only
    func createContent()      // ContentCreator only
    func viewContent()        // All users
}

// Different user classes are forced to implement unnecessary methods
class Admin: User {
    func manageUsers() {
        print("Admin managing users")
    }

    func createContent() {
        print("Admin creating content")
    }

    func viewContent() {
        print("Admin viewing content")
    }
}

class ContentCreator: User {
    func manageUsers() {
        // Not needed, but must implement
    }

    func createContent() {
        print("Content Creator creating content")
    }

    func viewContent() {
        print("Content Creator viewing content")
    }
}

class Viewer: User {
    func manageUsers() {
        // Not needed, but must implement
    }

    func createContent() {
        // Not needed, but must implement
    }

    func viewContent() {
        print("Viewer viewing content")
    }
}
```
# Interface Segregation Principle (ISP) - Good Example

The Interface Segregation Principle (ISP) states that no client should be forced to depend on interfaces it does not use. To adhere to ISP, interfaces should be small and specific to the client's needs, rather than large and generalized.

## Good Example

In this example, the large `User` interface is split into smaller, more specific interfaces. Each class implements only the interfaces relevant to its role, adhering to the Interface Segregation Principle.

### Code Example

```swift
// Define smaller, more specific interfaces
protocol Manageable {
    func manageUsers()
}

protocol Creatable {
    func createContent()
}

protocol Viewable {
    func viewContent()
}

// Implement each user class to only include the interfaces it needs
class Admin: Manageable, Creatable, Viewable {
    func manageUsers() {
        print("Admin managing users")
    }

    func createContent() {
        print("Admin creating content")
    }

    func viewContent() {
        print("Admin viewing content")
    }
}

class ContentCreator: Creatable, Viewable {
    func createContent() {
        print("Content Creator creating content")
    }

    func viewContent() {
        print("Content Creator viewing content")
    }
}

class Viewer: Viewable {
    func viewContent() {
        print("Viewer viewing content")
    }
}



