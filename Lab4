# Lab 4 - Introduction to Software Testing

## Lab Summary
This lab focused on the fundamentals of software testing, with a practical emphasis on writing unit tests in Java using the JUnit framework. The exercises covered key testing concepts, types of tests, and hands-on examples of writing and running automated tests.

---

## Key Concepts

### Purpose of Software Testing
- Ensure software quality
- Identify bugs early
- Detect regressions after updates

### When to Test
- **Early and often**: Preferably during development
- **Test-Driven Development (TDD)**: Write tests before code
- **Bug-Driven Development (BDD)**: Write tests after bugs are found

### Categories of Tests

#### By Scope
| Type         | Description                                  | Examples                    |
|--------------|----------------------------------------------|-----------------------------|
| Unit         | Test individual functions/classes            | JUnit, pytest               |
| Integration  | Test interaction between components          | API endpoint tests          |
| System       | Test entire software system                  | UI flows                    |
| Acceptance   | Validate client requirements                 | User Acceptance Testing     |

#### By Execution Pattern
| Type        | Description                                  | Examples                    |
|-------------|----------------------------------------------|-----------------------------|
| Manual      | Human-performed tests                        | Exploratory testing         |
| Automated   | Scripted tests                               | JUnit, Selenium             |
| Continuous  | CI/CD pipeline tests                         | GitHub Actions, Jenkins     |

#### By Context
| Type   | Description                            | Examples              |
|--------|----------------------------------------|-----------------------|
| Static | No execution needed                    | Code review, linters  |
| Dynamic| Executed during runtime                | Unit tests, UI tests  |

#### By Purpose
| Type         | Description                                  | Examples                    |
|--------------|----------------------------------------------|-----------------------------|
| Functional   | Validate specific behaviors                  | Login, file upload          |
| Non-functional| Validate qualities like performance         | Load testing, security      |
| Regression   | Ensure new changes don’t break old features  | Full test suite             |
| Smoke/Sanity | Quick checks of critical features            | Startup, login              |
| Alpha/Beta   | Early user testing                           | Internal alpha, public beta |

#### By Special Focus
| Type           | Description                              | Examples                    |
|----------------|------------------------------------------|-----------------------------|
| Performance    | Speed, scalability, stability            | Load, stress tests          |
| Security       | Vulnerability detection                  | Penetration testing         |
| Compatibility  | Cross-platform support                   | Browser/OS testing          |
| Usability      | User experience                          | Feedback sessions           |
| Recovery       | Resilience under failure                 | Simulated crashes           |

---

##  Java Testing with JUnit

###  Setup
Add JUnit to Maven project:
```xml
<dependency>
  <groupId>org.junit.jupiter</groupId>
  <artifactId>junit-jupiter-api</artifactId>
  <version>6.0.0</version>
  <scope>test</scope>
</dependency>


---
## Writing Unit Tests
JUnit tests are:
- Written as methods in a test class
- Annotated with @Test
- Use assertions like assertTrue, assertFalse, assertEquals
Examples:
```java
@Test
public void testThatPrimesArePrime() {
  assertTrue(IntUtils.isPrime(2));
  assertTrue(IntUtils.isPrime(3));
  assertTrue(IntUtils.isPrime(251));
}
```
```java
@Test
public void testTakeDamage() {
  Hero hero = new Hero();
  hero.takeDamage(10);
  assertEquals(90, hero.getHealth());
}
```



