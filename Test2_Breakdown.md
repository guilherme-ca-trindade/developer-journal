# Summary of "Introduction to Software Testing" Lecture

## Main Topics Covered

### 1. **Purpose of Software Testing**
- Ensures software quality
- Identifies bugs early
- Prevents regressions
- Supports test-driven (TDD) and bug-driven (BDD) development approaches

### 2. **Types of Tests**
Tests are categorized by:

| Category          | Examples                                   |
|-------------------|--------------------------------------------|
| Scope             | Unit, Integration, System, Acceptance      |
| Execution Pattern | Manual, Automatic, Continuous              |
| Context           | Static, Dynamic                            |
| Purpose           | Functional, Non-functional, Regression, Smoke |
| Special Focus     | Performance, Security, Compatibility, Usability |

### 3. **Testing Frameworks**
Common frameworks by language:
- **Java**: JUnit, TestNG
- **C#/.NET**: xUnit, NUnit, MSTest
- **Python**: Pytest
- **JavaScript**: Jest, Mocha
- **Go**: `go test`
- **PHP**: PHPUnit, Pest

### 4. **Writing Automated Tests**
- Separate test programs verify expected outputs
- Tests should be clear, repeatable, and fast
- Use assertions to compare expected vs. actual results

### 5. **Unit Testing with JUnit (Java)**
- Annotations: `@Test`
- Assertions: `assertTrue()`, `assertEquals()`
- Test methods should be descriptive and focus on a single theme

### 6. **Choosing What to Test**
- Input validation (valid and invalid)
- Boundary conditions
- Special cases (null, zero, empty values)
- Exception handling
- Code coverage is ideal but prioritization is key

---

## Key Code Examples

### 1. **JUnit Test Structure**
```java
import org.junit.jupiter.api.Test;
import static org.junit.jupiter.api.Assertions.*;

class TestIntUtils {
    @Test
    public void testThatPrimesArePrime() {
        assertTrue(IntUtils.isPrime(2));
        assertTrue(IntUtils.isPrime(3));
        assertTrue(IntUtils.isPrime(251));
    }
}
```

### 2. **Testing Constructors and Methods**
```java
class HeroTest {
    @Test
    public void testConstructor() {
        var hero = new Hero();
        assertEquals(100, hero.getHealth());
    }

    @Test
    public void testTakeDamage() {
        var hero = new Hero();
        hero.takeDamage(10);
        assertEquals(90, hero.getHealth());
    }
}
```

### 3. **Testing String Functions**
```java
@Test
void testValidInputs() {
    assertEquals("Hello", StrUtils.titleCase("hello"));
    assertEquals("Hello", StrUtils.titleCase("HELLO"));
}

@Test
void nullRemainsNull() {
    assertNull(StrUtils.titleCase(null));
}
```

---

## Best Practices Highlighted
- Test early and often
- Write tests before code in TDD
- Include both positive and negative test cases
- Focus on high-risk and frequently used components
- Use descriptive test names
- Group related assertions in a single test

---

## Tools and Environment
- **IDE Support**: Run tests individually, by class, or all tests
- **Maven Integration**: Add JUnit as a test-scoped dependency
- **Continuous Integration**: Automated tests in CI/CD pipelines (e.g., GitHub Actions, Jenkins)

---

This lecture provides a foundational understanding of software testing principles, practical JUnit usage, and strategies for writing effective unit tests in Java and other languages.
