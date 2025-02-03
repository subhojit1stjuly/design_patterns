# Baic Object-Oriented Programming Concepts in Dart

## Coupling

Coupling determines how much one class depends on another class. High coupling can make a system difficult to maintain and modify.

### Example of Tight Coupling

```dart
class User {
  void sayHello() {
    print("hello");
  }
}

class Main {
  void main() {
    User user = User();
    user.sayHello();
  }
}
```

When we modify the `User` class by adding a constructor parameter:

```dart
class User {
  String name;
  
  User(this.name);
  
  void sayHello() {
    print("hello");
  }
}

class Main {
  void main() {
    User user = User("SomeName");
    user.sayHello();
  }
}
```

This demonstrates tight coupling - changes in one class force changes in another.

## Using Interfaces for Loose Coupling

Interfaces provide a contract that specifies what capabilities a class should provide.

```dart
abstract class TaxCalculator {
  float calculateTax();
}

class TaxCalculator2019 implements TaxCalculator {
  @override
  float calculateTax() {
    return 1;
  }
}

class TaxCalculator2020 implements TaxCalculator {
  @override
  float calculateTax() {
    return 2;
  }
}

void main() {
  TaxCalculator calculator = getCalculator();
  calculator.calculateTax();
}

TaxCalculator getCalculator() {
  return TaxCalculator2020();
}
```

## Four Pillars of OOP

### 1. Encapsulation

Bundling the data and methods that operates on that data into a single unit 
and hinding the values or state of the object inside the class, so that we can create robust apllication where we can prevent the object to go on an invalid state. 

```dart
class Account {
  double _balance = 0.0;

  double get balance => _balance;

  set deposit(double amount) {
    if (amount > 0) {
      _balance += amount;
    }
  }

  set withdraw(double amount) {
    if (amount < _balance) {
      _balance -= amount;
    }
  }
}
```

### 2. Abstraction

Hiding unnecessary implementation details to reduce complexity.

```dart
class MailService {
  void sendEmail(String address) {
    _connect();
    _authenticate();
    // Send email implementation
    _disconnect();
  }

  bool _connect() {
    return true;
  }
  
  bool _disconnect() {
    return true;
  }
  
  bool _authenticate() {
    return true;
  }
}
```

### 3. Inheritance

Mechanism for code reuse through class hierarchy.

```dart
class UIControl {
  void enable() {
    print("enabled");
  }
  
  void disable() {
    print("disabled");
  }
}

class TextBox extends UIControl {}
```

### 4. Polymorphism

Ability of objects to take multiple forms.

```dart
abstract class UIControl {
  void enable() {
    print("enabled");
  }
  
  void disable() {
    print("disabled");
  }
  
  void draw();
}

class TextBox extends UIControl {
  @override
  void draw() {
    print("TextBox drawn");
  }
}

class CheckBox extends UIControl {
  @override
  void draw() {
    print("CheckBox drawn");
  }
}

void drawUIControl(UIControl control) {
  control.draw();
}

void main() {
  drawUIControl(TextBox());
  drawUIControl(CheckBox());
}
```