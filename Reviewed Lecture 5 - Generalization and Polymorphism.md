# Summary of "Inheritance and Interfaces" Lecture

## Main Topics Covered

### 1. **Software Design Principles**
- **DRY (Don’t Repeat Yourself)**: Avoid repeating the same implementation, but not necessarily the same lines of code
- **Cohesion**: Degree to which parts of a component belong together
- **Coupling**: Degree to which components depend on each other
- **Single Responsibility Principle (SRP)**: A class should have one reason to change

### 2. **Abstraction and Encapsulation Review**
- **Abstraction**: Focusing on essential details, ignoring irrelevant complexity
- **Encapsulation**: Exposing an abstraction while hiding implementation details

### 3. **Generalization and Inheritance**
- **Generalization**: Sharing common details in a broader abstraction (e.g., a superclass)
- **Inheritance**: Subclasses inherit members from superclasses using `extends`
- **"Is-a" Relationship**: A subclass **is a** type of its superclass (e.g., `Student` is a `Person`)

### 4. **Visibility Modifiers**
| Modifier    | Class | Package | Subclass | Other |
|-------------|-------|---------|----------|-------|
| `private`   | ✓     | X       | X        | X     |
| (default)   | ✓     | ✓       | X        | X     |
| `protected` | ✓     | ✓       | ✓        | X     |
| `public`    | ✓     | ✓       | ✓        | ✓     |

- `protected` allows subclasses to access members, even in different packages

### 5. **Constructors in Inheritance**
- Constructors are called from the top of the hierarchy downward
- Use `super()` to call a superclass constructor (must be first statement)
- Default constructor is called automatically if not specified

### 6. **Method Overriding**
- Subclass provides a specialized implementation of a superclass method
- Must have the same signature
- Use `@Override` annotation for clarity and compile-time checking
- Use `super.method()` to call the superclass version

### 7. **Overriding vs Overloading**
- **Overriding**: Same method signature in subclass
- **Overloading**: Same method name, different signatures in the same class

### 8. **Static Type vs Runtime Type**
- **Static Type**: Declared type of the variable (checked at compile time)
- **Runtime Type**: Actual type of the object instantiated (determined at runtime)

### 9. **Dynamic Method Dispatch**
- Runtime determines which overridden method to call based on the **runtime type**
- Enables **subtype polymorphism**: treating subclass objects as superclass types while using their specific implementations

**Example:**
```java
Person p = new Instructor();
p.toString(); // Calls Instructor.toString() at runtime
```

### 10. **Subtype Polymorphism**
- Allows uniform interaction with different types through a common interface
- Enables code reuse and flexibility

**Example:**
```java
List<Animal> animals = new ArrayList<>();
animals.add(new Dog());
animals.add(new Cat());
for (Animal a : animals) {
    a.makeSound(); // Calls Dog.makeSound() or Cat.makeSound()
}
```

### 11. **Abstract Classes**
- Cannot be instantiated directly
- May contain abstract methods (no implementation)
- Subclasses must implement all abstract methods (or be abstract themselves)

**Example:**
```java
abstract class Storage {
    public abstract void write(String data);
}

class Disk extends Storage {
    @Override
    public void write(String data) {
        // Disk-specific implementation
    }
}
```

### 12. **Design Principles Revisited**
- **Open/Closed Principle**: Classes should be open for extension, closed for modification
- **Liskov Substitution Principle (LSP)**: Subtypes should be replaceable for supertypes without altering program behavior

---

## Key Code Examples

### 1. **Generalization with Inheritance**
```java
class Person {
    protected String name;
    protected String address;
    
    public String letterhead() {
        return name + address;
    }
}

class Student extends Person {
    private Program program;
    // Inherits name, address, and letterhead()
}
```

### 2. **Method Overriding**
```java
class Person {
    @Override
    public String toString() {
        return name;
    }
}

class Instructor extends Person {
    @Override
    public String toString() {
        return super.toString() + " (Instructor)";
    }
}
```

### 3. **Dynamic Method Dispatch Example**
```java
Person p1 = new Student();
Person p2 = new Instructor();

p1.toString(); // Calls Student.toString()
p2.toString(); // Calls Instructor.toString()
```

### 4. **Abstract Class**
```java
abstract class Animal {
    public abstract void makeSound();
}

class Dog extends Animal {
    @Override
    public void makeSound() {
        System.out.println("Woof!");
    }
}
```

### 5. **Using Polymorphism in Collections**
```java
List<Person> people = new ArrayList<>();
people.add(new Student());
people.add(new Instructor());

for (Person p : people) {
    System.out.println(p.toString()); // Dynamic dispatch
}
```

---

## Best Practices Highlighted
- Use inheritance for true "is-a" relationships
- Favor composition over inheritance when possible
- Keep inheritance hierarchies shallow
- Use `@Override` for clarity
- Follow LSP to ensure substitutability
- Design for loose coupling and high cohesion

---

## Important Terms to Remember
- **Generalization**: Creating a superclass from commonalities
- **Inheritance**: `extends` keyword, subclass inherits superclass members
- **Polymorphism**: Uniform interface for different types
- **Dynamic Method Dispatch**: Runtime selection of overridden method
- **Abstract Class**: Cannot instantiate, may have abstract methods
- **Liskov Substitution Principle**: Subtypes should be replaceable

---

This lecture builds a strong foundation in OOP principles, focusing on how inheritance, polymorphism, and abstraction work together to create maintainable, extensible, and reusable software designs.
