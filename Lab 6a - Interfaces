# Summary of "Interfaces" Lecture

## Main Topics Covered

### 1. **What are Interfaces?**
- Define **behaviour only** (methods) without shared state
- Enable abstraction without inheritance
- All methods are `public` and `abstract` by default (no implementation)
- Classes can implement **multiple interfaces**

### 2. **Defining and Implementing Interfaces**
```java
public interface Alerter {
    void alert(String message);
}

public class EmailAlerter implements Alerter {
    @Override
    public void alert(String message) {
        // Send email
    }
}
```

### 3. **Default Methods**
- Interfaces can provide default implementations
- Use `default` keyword
- Implementing classes can override them
```java
public interface Service {
    void doSomething();
    default void doDefault() {
        // Default implementation
    }
}
```

### 4. **Benefits of Interfaces**
- **Modularity**: Code depends on abstractions, not concrete implementations
- **Flexibility**: New implementations can be added without modifying existing code
- **Polymorphism**: Different implementations can be used interchangeably

### 5. **Interface Segregation Principle (ISP)**
- **Principle**: Clients should not be forced to depend on methods they don't use
- **Solution**: Create smaller, focused interfaces
- **Violation Example**:
```java
// BAD: Circle doesn't need 3D methods
interface Shape {
    void area();
    void volume();
}
```
- **Improved**:
```java
interface Shape2D { void area(); }
interface Shape3D { void volume(); }
class Circle implements Shape2D { ... }
```

### 6. **Dependency Inversion Principle (DIP)**
- **Principle**: 
  1. High-level modules should not depend on low-level modules (both should depend on abstractions)
  2. Abstractions should not depend on details (details should depend on abstractions)
- **Violation Example**:
```java
// High-level depends on low-level
class Foo {
    private Logger logger = new Logger();  // Direct dependency
}
```
- **Improved with Dependency Injection**:
```java
interface ILogger { void log(String msg); }
class Logger implements ILogger { ... }

class Foo {
    private ILogger logger;
    public Foo(ILogger logger) {  // Dependency injected
        this.logger = logger;
    }
}
```

### 7. **Dependency Injection (DI)**
- **Definition**: Passing dependencies as parameters rather than instantiating them internally
- **Types**: Constructor injection, setter injection, field injection
- **Benefits**: Loose coupling, easier testing, more flexible code

### 8. **Design Patterns Using Interfaces**

#### **Strategy Pattern**
- **Problem**: Need different algorithms/behaviours for a task
- **Solution**: Define strategy interface, implement concrete strategies
```java
interface PaymentStrategy {
    void pay(double amount);
}

class CreditCardPayment implements PaymentStrategy { ... }
class PayPalPayment implements PaymentStrategy { ... }

class ShoppingCart {
    private PaymentStrategy payment;
    public void setPayment(PaymentStrategy payment) {
        this.payment = payment;
    }
}
```

#### **Observer Pattern**
- **Problem**: One object needs to notify many others of changes
- **Solution**: Subject maintains list of observers, notifies via interface
```java
interface ClickHandler {
    void handleClick();
}

class Button {
    private List<ClickHandler> handlers = new ArrayList<>();
    
    public void addClickHandler(ClickHandler handler) {
        handlers.add(handler);
    }
    
    public void click() {
        for (ClickHandler h : handlers) {
            h.handleClick();
        }
    }
}
```

### 9. **Key Terminology**
| Term | Definition |
|------|------------|
| **Interface** | Code structure defining methods implementers must provide |
| **API** | Any programmable interface (class, library, web service) |
| **Public Interface** | Public members of a class |
| **Function Interface** | Signature of a function (name, params, return type) |

### 10. **Best Practices**
- Follow **Single Responsibility Principle** for interfaces
- Use **Interface Segregation** to create focused interfaces
- Apply **Dependency Inversion** to depend on abstractions
- Use **Dependency Injection** for loose coupling
- Implement **Strategy Pattern** for interchangeable algorithms
- Use **Observer Pattern** for event notification systems

---

## Key Code Examples

### 1. **Basic Interface Implementation**
```java
public interface Drawable {
    void draw();
    default void resize() {
        System.out.println("Resizing...");
    }
}

public class Circle implements Drawable {
    @Override
    public void draw() {
        System.out.println("Drawing circle");
    }
}
```

### 2. **Strategy Pattern Example**
```java
interface SortingStrategy {
    void sort(int[] array);
}

class QuickSort implements SortingStrategy {
    @Override
    public void sort(int[] array) {
        // Quick sort implementation
    }
}

class ArraySorter {
    private SortingStrategy strategy;
    
    public ArraySorter(SortingStrategy strategy) {
        this.strategy = strategy;
    }
    
    public void sortArray(int[] array) {
        strategy.sort(array);
    }
}
```

### 3. **Dependency Injection Example**
```java
// Service interface
interface DataService {
    String fetchData();
}

// Concrete implementation
class DatabaseService implements DataService {
    @Override
    public String fetchData() {
        return "Data from database";
    }
}

// Client class using DI
class DataProcessor {
    private DataService service;
    
    // Constructor injection
    public DataProcessor(DataService service) {
        this.service = service;
    }
    
    public void process() {
        String data = service.fetchData();
        // Process data
    }
}
```

---

## Important Concepts to Remember
1. **Interfaces define contracts** - what a class can do, not how
2. **Multiple inheritance** is possible with interfaces (not with classes)
3. **Default methods** allow adding functionality without breaking existing code
4. **ISP** prevents "fat interfaces" with unrelated methods
5. **DIP** decouples high-level and low-level modules
6. **DI** makes code testable and flexible
7. **Strategy Pattern** enables runtime algorithm selection
8. **Observer Pattern** facilitates event-driven programming

---

This lecture demonstrates how interfaces enable flexible, maintainable, and testable software design through abstraction, dependency management, and design patterns.
