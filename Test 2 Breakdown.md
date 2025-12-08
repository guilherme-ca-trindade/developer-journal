# 📝 Java OOP & Design Principles Cheat Sheet

---

## 1. Overriding & @Override
- **Overriding**: Subclass redefines a method from superclass.
- **@Override**: Ensures compile‑time check, prevents silent mistakes.

```java
class A {
    void sayHello() { System.out.println("Hello from A"); }
}
class B extends A {
    @Override
    void sayHello() { System.out.println("Hello from B"); }
}
```

---

## 2. toString & Object Printing
• Default: ClassName@hashcode
• Override for meaningful output.

```java
class Person {
    private String name;
    public Person(String name) { this.name = name; }
    @Override
    public String toString() { return name; }
}
System.out.println(new Person("Bob")); // Bob
```

---

## 3. Inheritance & Polymorphism

• Upcasting: Subclass → Superclass reference ✅
• Downcasting: Superclass → Subclass reference ❌ (unsafe unless actual type matches)

```java
A a = new C(); // OK
C c = new A(); // Compile error
```

---

## 4. Field Hiding vs Method Overriding

• Method overriding → runtime polymorphism.
• Field hiding → compile‑time resolution, confusing, avoid.

```java
class A { int x = 1; }
class B extends A { int x = 2; } // hides A.x
```

---

## 5. Interfaces

• Define contracts, no implementation (except default/static).
• Methods are implicitly public abstract.

```java
interface Steerable { void turn(int degrees); }
interface Drivable { void go(); void stop(); }
```

---

## 6. Dependency Injection & Testability

• Pass dependencies via constructor → easier to test.

```java
class UserService {
    private Database db;
    UserService(Database db) { this.db = db; }
    void register() { db.save(); }
}
```

---

## 7. Single Responsibility Principle (SRP)

• A class should have one reason to change.
• Example: UserService handles user logic, not DB creation.


---

## 8. JavaFX Panes

• Layout containers for arranging UI nodes.
• Examples:• FlowPane → sequential flow
• BorderPane → top/bottom/left/right/center
• GridPane → rows/columns


```java
FlowPane pane = new FlowPane();
pane.getChildren().add(new Button("Click Me"));
```

---

## 9. String Formatting

• %s → String
• %d → Integer
• %f → Floating point
• %c → Character
• %tX → Date/Time

```java
System.out.printf("Name: %s, Age: %d%n", "Bob", 30);
System.out.println("The %s turned %d degrees.".formatted("Car", 10));
```

---

## 10. JDK 25 IO Utility

• Simplifies console I/O.

```java
IO.println("Hello!");
String name = IO.readln("Enter your name: ");
IO.println("Welcome, " + name);
```

---

## 11. Point & LabelledPoint Example

• Encapsulation, inheritance, overriding.

```java
class Point {
    protected int x, y;
    public Point(int x, int y) { this.x = x; this.y = y; }
    @Override public String toString() { return "(" + x + "," + y + ")"; }
}

class LabelledPoint extends Point {
    private String label;
    public LabelledPoint(int x, int y, String label) { super(x,y); this.label = label; }
    @Override public String toString() { return label + ":" + super.toString(); }
}
```

---

## 12. Design Guidelines

• Use @Override consistently.
• Prefer dependency injection over new.
• Keep interfaces small (Interface Segregation).
• Avoid field hiding.
• Respect Liskov Substitution Principle (subtypes must behave like supertypes).
• Separate UI, domain, infrastructure (SRP).



---

# Object-oriented foundations and method behavior

## Overriding and the @Override annotation

• Purpose: Overriding lets a subclass provide a new implementation for a method defined in its superclass, enabling polymorphic behavior.
• Signature matching: A method overrides only if the name, parameter types, and return type (covariant allowed) match the inherited method. Access must be at least as visible; you cannot reduce visibility.
• @Override as a safeguard: The annotation isn’t required but adds a compile-time check. If the method doesn’t truly override, compilation fails, preventing subtle bugs due to typos or signature mismatches.
• Dynamic dispatch: At runtime, the most specific override is chosen based on the actual object type, not the reference type.


## toString, object printing, and class contracts

• Default behavior: Printing an object calls toString(); if not overridden, it returns ClassName@hashcode.
• Custom representation: Override toString() to provide a meaningful, stable textual representation. Keep it side-effect-free and fast.
• Design tip: Prefer toString() for debugging and logging; for external formats or user-facing strings with localization, use dedicated formatters.


## Inheritance, polymorphism, and assignability

• Upcasting: You can assign a subclass instance to a superclass reference (e.g., A x = new C()), enabling polymorphic use of common operations.
• Downcasting: Assigning a superclass instance to a subclass reference requires a cast and is only safe if the object is actually an instance of the subclass; otherwise, it fails at runtime.
• Liskov Substitution Principle (LSP): Subtypes must preserve the expectations of supertypes; overridden behavior should not violate the superclass contract.


## Field hiding vs method overriding

• Method overriding: Changes behavior polymorphically; calls resolve at runtime.
• Field hiding: Re-declaring an instance variable in a subclass hides the superclass field, which is confusing and resolved at compile time based on reference type. Avoid re-declaring fields; reuse inherited state or refactor.


---

## Interfaces, visibility, and design principles

### Interfaces as behavioral contracts

• Abstraction level: Interfaces define “what” (capabilities) without “how” (implementation), keeping components decoupled.
• Members: Method signatures (implicitly public abstract), constants (public static final), plus default, static, and private helper methods in modern Java.
• Extension: Interfaces can extend other interfaces; multiple inheritance of type is allowed.


### Implementations must be public

• Visibility rule: Methods implementing interface methods must be public. Using protected or private breaks the contract and does not compile.
• Substitutability: Public methods ensure any implementing class is usable wherever the interface is expected.


###  Steerable and Drivable contracts

• Separation of concerns: Define focused interfaces: Steerable (turn behavior) and Drivable (motion control). A Vehicle composes these abilities.
• Interface segregation: Clients depend only on methods they use, improving flexibility and testability.


### Single Responsibility Principle (SRP)

• Definition: A class or module should have one reason to change—one focused responsibility.
• Applied examples:• UserService: Should orchestrate user registration logic, not create or manage database connections directly.
• Vehicle: Responsible for vehicle behavior, not for UI I/O, persistence, or logging format details.

• Benefits: Easier testing, clearer maintenance, reduced coupling, and cleaner boundaries for dependency management.


---

## Testability, dependency injection, and coupling

### Dependency injection (DI)

• Concept: Pass dependencies (e.g., Database) into constructors or setters rather than constructing them internally.
• Advantages: Enables mocking/stubbing in tests, reduces coupling to concrete classes, and improves modularity.
• Patterns: Constructor injection (preferred), setter injection (optional for optional deps), and interface-based programming to depend on abstractions.


### Coupling and cohesion

• Low coupling: Minimize knowledge about other modules; depend on interfaces rather than concrete implementations.
• High cohesion: Group related responsibilities within a class; don’t mix unrelated concerns.


---

## JavaFX layout fundamentals

### Panes and layout management

• Role: A Pane is a container that holds and arranges UI nodes. Different panes provide different layout strategies.
• Common panes:• FlowPane: Positions nodes sequentially and wraps them.
• BorderPane: Top, bottom, left, right, center regions.
• GridPane: Row/column layout for forms and tables.
• VBox/HBox: Vertical/horizontal stacks.

• Separation from styling: Layout is distinct from styling (CSS) and event handling; keep concerns separated for clarity.


---

## Console I/O and string formatting in modern Java

### JDK 25 IO utility

• Convenience: Simple static methods like IO.println() and IO.readln() streamline console programs without System.out or Scanner.
• Usage boundaries: Ideal for small apps and teaching; for robust CLIs, consider structured logging and input validation layers.


### String formatting and interpolation

• APIs:• String.format(...) / System.out.printf(...): Classic printf-style.
• "template".formatted(args...): Modern, concise alternative (JDK 21+).
• Text blocks: Triple-quoted multi-line strings combined with .formatted(...) for clean templates.

• Specifiers:• %s: String (calls toString()).
• %d: Decimal integer.
• %f: Floating point with precision options.
• %c: Character or Unicode code point.
• %b: Boolean.
• %tX: Date/time with a conversion (%tY year, %tB month name, %tH hour, etc.).

• Type safety: Specifier must match argument type; mismatches throw IllegalFormatConversionException.
• Reusability: Use the < flag to reuse the previous argument in complex date/time formats.


---

## Class design: Point and LabelledPoint

### Encapsulation and representation

• State: Point holds x and y; LabelledPoint adds label.
• Constructors: Initialize required state clearly and completely; call super from subclasses.
• toString overrides: Provide readable, deterministic representations: (x,y) and label:(x,y).


### Getters and setters

• When to include: Add getters/setters if external mutation or access is required; otherwise keep fields immutable.
• Immutability: Consider making fields final and omitting setters to prevent unintended changes and simplify reasoning.


### Simplifying while keeping clarity

• Protected vs private: Use protected for fields only when subclasses need direct access; prefer private with protected getters for cleaner encapsulation.
• Records (where suitable): For simple data carriers, record Point(int x, int y) provides immutability, equals/hashCode/toString automatically. Subclassing records is limited; use composition for LabelledPoint if adopting records.


---


