# UML (Unified Modeling Language)

UML is the standard language for modeling object-oriented systems. It provides a way to visualize the architectural blueprints of your system.

## Class Representation

### Basic UML Class Structure

```
+-----------------+
|     Shape       |  <- Class name
+-----------------+
| - positionX: int|  <- Fields (properties)
+-----------------+
| + render(): void|  <- Methods
+-----------------+
```

### Dart Implementation
```dart
class Shape {
    int _positionX = 0;
    
    Shape(int position) {
        _positionX = position;
    }
    
    void render() {
        // Implementation
    }
}
```

## Class Relationships

### 1. Inheritance
Represented by an empty arrow (▷)

```
Rectangle ─────▷ Shape
```

```dart
class Rectangle extends Shape {
    // Rectangle implementation
}
```

### 2. Composition
Represented by a filled diamond arrow (♦→)

```
Shape ♦──────> Size
```

```dart
class Shape {
    final Size size;
    
    Shape(this.size);
}
```

### 3. Aggregation
Represented by an empty diamond arrow (◇→)

```
Department ◇──────> Employee
```

Example of Aggregation:
```
+---------------+         +-------------+
|   Department  |  ◇───> |  Employee   |
+---------------+         +-------------+
| - name        |         | - name     |
| - employees   |         | - id       |
+---------------+         +-------------+
```

```dart
class Employee {
    final String name;
    final int id;
    
    Employee(this.name, this.id);
}

class Department {
    final String name;
    final List<Employee> employees;
    
    Department(this.name, [List<Employee>? employees])
        : employees = employees ?? [];
        
    void addEmployee(Employee employee) {
        employees.add(employee);
    }
    
    void removeEmployee(Employee employee) {
        employees.remove(employee);
    }
}
```

### 4. Dependency
Represented by a dashed arrow (--→)

```
Shape - - - -> Document
```

```dart
class Shape {
    void render(Document doc) {
        // Implementation using Document
    }
}
```

## UML Visibility Modifiers

- `+` Public
- `-` Private
- `#` Protected
- `~` Package/Internal

## Best Practices

1. Keep diagrams simple and focused
2. Use consistent notation
3. Include only relevant details
4. Document relationships clearly
5. Use appropriate visibility modifiers


