# Summary of "Lambdas and Higher-Order Functions" Lecture

## Main Topics Covered

### 1. **Higher-Order Functions in Java**
- Java doesn't have true higher-order functions, but provides syntax that mimics them via **functional interfaces** and **lambda expressions**
- **Example:**
```java
list.forEach(item -> System.out.println(item));
```

### 2. **Functional Interfaces**
- **Definition**: Any interface with **exactly one** abstract (non-default) method
- Can have multiple default methods, but only one abstract method
- **@FunctionalInterface** annotation provides compile-time checking

```java
@FunctionalInterface
public interface MathOp {
    double calc(double x, double y);
    // Only ONE abstract method allowed
    default void log() { System.out.println("Logging"); } // OK
}
```

### 3. **Lambda Expressions**
- Concise syntax for implementing functional interfaces
- **Basic syntax**: `(parameters) -> { body }`
- **Simplified forms**:
```java
// Full form
MathOp multiply = (x, y) -> { return x * y; };

// Single expression (return implicit)
MathOp multiply = (x, y) -> x * y;

// Single parameter (no parentheses needed)
UnaryMathOp doubler = x -> x * 2;

// No parameters
Supplier<Double> random = () -> Math.random();
```

### 4. **Using Lambda Expressions**
- Can be used anywhere a functional interface is expected
```java
public void doMath(double x, double y, MathOp op) {
    System.out.println(op.calc(x, y));
}

// Pass lambda directly
doMath(5, 10, (x, y) -> x * y);
```

### 5. **Common Functional Interfaces in JDK**
| Interface | Description | Example |
|-----------|-------------|---------|
| `Consumer<T>` | Accepts T, returns void | `s -> System.out.println(s)` |
| `Supplier<T>` | No params, returns T | `() -> Math.random()` |
| `Function<T,R>` | Accepts T, returns R | `s -> s.length()` |
| `BiFunction<T,U,R>` | Accepts T and U, returns R | `(a, b) -> a + b` |
| `Predicate<T>` | Accepts T, returns boolean | `s -> s.length() > 5` |

### 6. **Method References**
- Shorter syntax for calling existing methods
- **Syntax**: `ClassName::methodName`
```java
// Static method
list.forEach(Integer::parseInt);          // (str) -> Integer.parseInt(str)

// Instance method (on class)
list.forEach(String::length);             // (str) -> str.length()

// Instance method (on object)
list.forEach(person::getName);            // () -> person.getName()

// Constructor
list.forEach(Person::new);                // (name, age) -> new Person(name, age)
```

### 7. **Anonymous Inner Classes**
- Under the hood, lambda expressions are converted to anonymous inner classes
- **Before Java 8**:
```java
list.forEach(new Consumer<String>() {
    @Override
    public void accept(String s) {
        System.out.println(s);
    }
});
```
- **After Java 8 (lambda)**:
```java
list.forEach(s -> System.out.println(s));
```

### 8. **Stream API**
- Provides functional-style operations on collections
- **Key operations**:

#### **Chainable (Intermediate) Operations**
| Operation | Description | Example |
|-----------|-------------|---------|
| `filter` | Keep items matching predicate | `.filter(s -> s.length() > 5)` |
| `map` | Transform each item | `.map(s -> s.toUpperCase())` |
| `distinct` | Remove duplicates | `.distinct()` |
| `sorted` | Sort items | `.sorted((a, b) -> a - b)` |
| `limit` | Keep first n items | `.limit(10)` |
| `skip` | Skip first n items | `.skip(5)` |

#### **Terminal Operations**
| Operation | Description | Example |
|-----------|-------------|---------|
| `forEach` | Perform action on each | `.forEach(System.out::println)` |
| `count` | Count items | `.count()` |
| `collect` | Convert to collection | `.collect(Collectors.toList())` |
| `reduce` | Accumulate values | `.reduce(0, (a, b) -> a + b)` |
| `anyMatch/allMatch` | Check conditions | `.anyMatch(s -> s.startsWith("A"))` |

### 9. **Practical Examples**

#### **Stream Pipeline**
```java
List<String> foods = List.of("apple", "banana", "cherry", "durian", "elderberry");

foods.stream()
    .filter(food -> food.length() > 5)      // Keep long names
    .map(String::toUpperCase)               // Convert to uppercase
    .sorted()                               // Sort alphabetically
    .forEach(System.out::println);          // Print each
// Output: BANANA, CHERRY, DURIAN, ELDERBERRY
```

#### **Reduction Example**
```java
List<Integer> numbers = List.of(1, 2, 3, 4, 5);

int sum = numbers.stream()
    .reduce(0, (a, b) -> a + b);  // Sum all numbers

long count = numbers.stream()
    .filter(n -> n % 2 == 0)      // Count even numbers
    .count();
```

#### **GUI Event Handling**
```java
// Traditional anonymous class
button.addActionListener(new ActionListener() {
    @Override
    public void actionPerformed(ActionEvent e) {
        System.out.println("Clicked!");
    }
});

// Lambda expression
button.addActionListener(e -> System.out.println("Clicked!"));
```

### 10. **Key Concepts to Remember**
1. **Functional interfaces** have exactly one abstract method
2. **Lambda expressions** provide concise implementation of functional interfaces
3. **Method references** are shorthand for calling existing methods
4. **Streams** enable functional-style processing of collections
5. **Operations are either intermediate** (return stream, can be chained) or **terminal** (return result, end chain)
6. **Under the hood**, lambdas become anonymous inner classes

---

## Important Code Patterns

### 1. **Creating Custom Functional Interface**
```java
@FunctionalInterface
interface StringProcessor {
    String process(String input);
    
    default void log(String msg) {
        System.out.println("Log: " + msg);
    }
}

// Usage
StringProcessor toUpper = s -> s.toUpperCase();
String result = toUpper.process("hello");  // "HELLO"
```

### 2. **Using Predicates**
```java
Predicate<String> isLong = s -> s.length() > 10;
List<String> longWords = words.stream()
    .filter(isLong)
    .toList();
```

### 3. **Function Composition**
```java
Function<String, Integer> length = String::length;
Function<Integer, Integer> doubleIt = n -> n * 2;

Function<String, Integer> doubleLength = length.andThen(doubleIt);
int result = doubleLength.apply("hello");  // 10
```

---

## Best Practices
1. Use **@FunctionalInterface** annotation for clarity
2. Prefer **method references** over lambdas when calling existing methods
3. Keep **lambda bodies short** (extract complex logic to methods)
4. Use **meaningful parameter names** in lambdas
5. **Chain stream operations** for readability
6. **Close streams** properly (they implement AutoCloseable)

---

This lecture demonstrates how Java provides functional programming capabilities through functional interfaces, lambda expressions, and the Stream API, enabling more concise, readable, and expressive code.
