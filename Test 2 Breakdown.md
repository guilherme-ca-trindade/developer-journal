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

2. toString & Object Printing

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

3. Inheritance & Polymorphism

• Upcasting: Subclass → Superclass reference ✅
• Downcasting: Superclass → Subclass reference ❌ (unsafe unless actual type matches)

```java
A a = new C(); // OK
C c = new A(); // Compile error
```

---

4. Field Hiding vs Method Overriding

• Method overriding → runtime polymorphism.
• Field hiding → compile‑time resolution, confusing, avoid.

```java
class A { int x = 1; }
class B extends A { int x = 2; } // hides A.x
```

---

5. Interfaces

• Define contracts, no implementation (except default/static).
• Methods are implicitly public abstract.

```java
interface Steerable { void turn(int degrees); }
interface Drivable { void go(); void stop(); }
```

---

6. Dependency Injection & Testability

• Pass dependencies via constructor → easier to test.

```java
class UserService {
    private Database db;
    UserService(Database db) { this.db = db; }
    void register() { db.save(); }
}
```

---

7. Single Responsibility Principle (SRP)

• A class should have one reason to change.
• Example: UserService handles user logic, not DB creation.


---

8. JavaFX Panes

• Layout containers for arranging UI nodes.
• Examples:• FlowPane → sequential flow
• BorderPane → top/bottom/left/right/center
• GridPane → rows/columns


```java
FlowPane pane = new FlowPane();
pane.getChildren().add(new Button("Click Me"));
```

---

9. String Formatting

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

10. JDK 25 IO Utility

• Simplifies console I/O.

```java
IO.println("Hello!");
String name = IO.readln("Enter your name: ");
IO.println("Welcome, " + name);
```

---

11. Point & LabelledPoint Example

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

12. Design Guidelines

• Use @Override consistently.
• Prefer dependency injection over new.
• Keep interfaces small (Interface Segregation).
• Avoid field hiding.
• Respect Liskov Substitution Principle (subtypes must behave like supertypes).
• Separate UI, domain, infrastructure (SRP).



---
