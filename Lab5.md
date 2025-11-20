# Lab 5 - TicTacToe game, Generalization and Polymorphism

## Lab Summary
In this lab, I extended a TicTacToe game by implementing new AI player types (`OmolaPlayer`, `CircePlayer`, `RandyPlayer`, etc.) without modifying the core game logic. This demonstrated the power of abstraction, polymorphism, and clean object-oriented design.

---

## Key Concepts to Remember

### 1. **Abstraction**
- The `Player` class defines an abstract method:
  ```java
  > public abstract Position pickNextMove(Board board);

- This allows all subclasses to implement their own strategy while the game logic stays generic.

### 2. Polymorphism
- In TicTacToeGame.doNextTurn, we use:
> Player whoseTurn = ...;
> Position move = whoseTurn.pickNextMove(board);

- This works regardless of whether whoseTurn is a HumanPlayer, RandyPlayer, or OmolaPlayer.

### 3. Encapsulation
- Each player class contains its own logic for choosing a move.
- The game engine doesn’t need to know how the decision is made — it just asks for a move.

### 4. Open/Closed Principle
- The system is open for extension (new players), but closed for modification (no changes to Main or TicTacToeGame).

## Logic Patterns in OmolaPlayer
### Strategy:
- Try to win
- Try to block opponent
- Pick a random fallback (center > corners > edges)
### Key Code:
> Board copy = new Board(board); // simulate move safely
> copy.place(pos, myToken);
> if (copy.getWinner() == myToken) return pos;

### Randomness:
- Used Collections.shuffle(...) to randomize fallback choices.
- Ensured fairness by testing that all fallback positions are eventually chosen.

### To Remember: 
- Use copy constructors to simulate moves without mutating state.
- Always check the declared type when calling methods (e.g., Player must declare pickNextMove).
- Favor abstract classes and polymorphism to keep game logic clean and extensible.

---
# Syntax and Logic Highlights

## Collections Class and Its Use

#### What is `Collections`?
The `Collections` class is a utility class in `java.util` that provides static methods for operating on collections like `List`, `Set`, and `Map`. It includes methods for sorting, shuffling, reversing, and more.

### Key Method Used: `Collections.shuffle(...)`
In `OmolaPlayer`, I used:
```java
> Collections.shuffle(shuffledCorners);

## List vs Map - Structure and Use
### What is a `List`?
A List is an ordered collection of elements.
- Access elements by index
- Store duplciates 
- Iterates in order

###Example for OmolaPlayer:
```java
List<Position> corners = List.of(
  new Position (Row.Top, Col.Left),
  new Position (Row.Top, Col.Right),
  new Position (Row.Bottom, Col.Left),
  new Position (Row.Bottom, Col.Right)
);
List<Position> shuffledCorners = new ArrayList<>(corners);
Collections.shuffle (shuffledCorners);
```
I used to store adn randomize the fallback movement option (center > corners > edges)

### What is a `Map`?
A Map is a collection of key-value pairs.
- Look up a value by its key
- Key must be unique
- Values can be any object

### Example for the code:
```java
Map<String, Supplier<Player>> playerMap = Map.of(
  "randy", () -> new RandyPlayer("Randy"),
  "circe", () -> new CircePlayer("Circe"),
  "linus", () -> new LinusPlayer("Linus"),
  "omola", () -> new OmolaPlayer("Omola")
);
Player player = playerMap.get(input).get();
>> The `Map` in Java is conceptually similar to the `Dictionary` in Python. To make the lab, I still prefer to use a List rather than a Map, due to familiarity.

## Ternary Operator
The ternary operator uses the syntax:
```java
condition ? valueIfTrue : valueIfFalse;
```

It evaluates the condition. If it's true, it returns valueIfTrue; otherwise, it returns valueIfFalse. It similar to a If/Else statement but with less coding and same functionality

### Using if/else:
```java
int score = 85;
String result;

if (score >= 60) {
    result = "Pass";
} else {
    result = "Fail";
}
```

### Using ternary operator:
```java
int score = 85;
String result = (score >= 60) ? "Pass" : "Fail";
```
### Other example:
```java
boolean isMember = true;
double price = isMember ? 9.99 : 14.99;
```
If isMember is true, price is 9.99; otherwise, it's 14.99.

### When to Use It
Use the ternary operator when:
- You need a quick decision between two values.
- The logic is simple and readable.
- You're assigning a value based on a condition.
Avoid it when:
- The logic is complex or nested.
- Readability suffers (especially for beginners).












