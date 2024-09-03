# Payment Processing System

## Overview

This payment processing system supports multiple payment methods including credit card, PayPal, and cryptocurrency. The system allows processing payments through different methods but does not follow the Open/Closed Principle. This means that adding new payment methods requires modifying the existing `PaymentProcessor` class.



# Payment Processing System

This Swift project demonstrates a payment processing system that adheres to the Open/Closed Principle, which is part of the SOLID design principles. The goal is to design a system that is flexible and extensible, allowing new payment methods to be added without modifying existing code.

## Open/Closed Principle

The Open/Closed Principle states that a class should be open for extension but closed for modification. This means that you should be able to extend the functionality of a class without altering its existing code.

## Example

The following example illustrates how to implement different payment methods while adhering to the Open/Closed Principle.

### PaymentMethod Protocol

Defines a common interface for all payment methods.

```swift
protocol PaymentMethod {
    func processPayment(amount: Double)
}
```
Concrete Payment Methods
Implementations of different payment methods.

CreditCardPayment
```swift
class CreditCardPayment: PaymentMethod {
    func processPayment(amount: Double) {
        print("Processing credit card payment of $\(amount)")
    }
}
```

PayPalPayment
```swift
class PayPalPayment: PaymentMethod {
    func processPayment(amount: Double) {
        print("Processing PayPal payment of $\(amount)")
    }
}
```
ApplePayPayment
```swift

class ApplePayPayment: PaymentMethod {
    func processPayment(amount: Double) {
        print("Processing Apple Pay payment of $\(amount)")
    }
}
```
PaymentProcessor Class
Manages a collection of payment methods and processes payments using these methods.

```swift
class PaymentProcessor {
    private var paymentMethods: [PaymentMethod] = []
    
    func addPaymentMethod(_ method: PaymentMethod) {
        paymentMethods.append(method)
    }
    
    func processAllPayments(amount: Double) {
        for method in paymentMethods {
            method.processPayment(amount: amount)
        }
    }
}

```
```swift
let paymentProcessor = PaymentProcessor()
paymentProcessor.addPaymentMethod(CreditCardPayment())
paymentProcessor.addPaymentMethod(PayPalPayment())
paymentProcessor.addPaymentMethod(ApplePayPayment())

paymentProcessor.processAllPayments(amount: 100.0)






