# Lab 6 – OOP Study Notes (Pokémon Type Analyzer)

Use this as a **review sheet** for your test: it focuses on the **main OOP concepts** and the **key ideas in your design**, not details of every line.

---

## 1. Big Picture: What Your Lab 6 App Does

- It is a **JavaFX GUI application** that:
  - Shows a **grid of Pokémon type buttons** (Normal, Fire, Water, etc.).
  - When you click a type, it shows a **detail view** with:
    - The type’s icon and name.
    - Lists of types that are:
      - **Super effective (2×)**
      - **Not very effective (0.5×)**
      - **No effect (0×)**
- Behind the scenes, it models Pokémon types using **inheritance, polymorphism, and a registry of singleton-like instances**.

---

## 2. Core OOP Concepts Demonstrated

### 2.1 Abstraction and Encapsulation (`PokemonType`)

- `PokemonType` is an **abstract base class** that represents *any* Pokémon type.
- It **encapsulates**:
  - Shared data: `name`, `imagePath`, `themeColor`.
  - Shared behavior: getters, effectiveness calculation method.
- It declares an **abstract method**:
  - `loadRelations()` → must be implemented by each specific type class to define strengths/weaknesses.
- Key ideas:
  - Abstract class = common template for all types.
  - Fields are `private`; access only via **getters**, which is encapsulation.
  - Subclasses don’t care *how* `effectivenessAgainst` is implemented; they only fill the lists that method uses.

**Study focus:**
- Why use an **abstract class** instead of a concrete one?
- Why keep fields `private` and expose only getters?

---

### 2.2 Inheritance (Concrete Type Classes)

- Each real Pokémon type (Fire, Water, Grass, etc.) is a **subclass** of `PokemonType`.
- Example pattern (conceptually):

  ```java
  class SomeType extends PokemonType {
      public SomeType() {
          super("SOME_TYPE", "/path.png", "#HEXCOLOR");
      }

      @Override
      public void loadRelations() {
          // add types this is strong/weak against
      }
  }
  ```

- They all:
  - Call `super(...)` in the constructor to set shared properties.
  - Override `loadRelations()` to fill in:
    - `superEffective`
    - `notVeryEffective`
    - `noEffect`

**Study focus:**
- How subclasses use `super(...)` to call the **superclass constructor**.
- How each subclass provides its **own specific data** while reusing the base class logic.

---

### 2.3 Polymorphism

**Static type**: `PokemonType`  
**Actual object**: `FireType`, `WaterType`, `GrassType`, etc.

- Arrays or lists are of type `PokemonType[]` or `List<PokemonType>`, but can hold any subtype.
- UI code never needs to know **which exact subclass** it’s dealing with; it just calls:
  - `getName()`
  - `getImagePath()`
  - `getThemeColor()`
  - `getSuperEffective()`, etc.

- When you call `loadRelations()` through a `PokemonType` reference, the **overridden version** in the correct subclass runs → **runtime polymorphism**.

**Study focus:**
- Be able to explain:  
  “We treat all types as `PokemonType`, but at runtime the correct subclass methods are used.”

---

### 2.4 Static Registry & Shared Instances (`TypeRegistry`)

- `TypeRegistry` holds **one shared instance** of each type as a `public static final` field.
- It uses a **static initializer block** to call `loadRelations()` on each type once at start-up.
- This design:
  - Avoids creating hundreds of duplicate type objects.
  - Gives a central place to reference the same instances everywhere (e.g., `TypeRegistry.FIRE`).

**Study focus:**
- Why `public static final` → behaves like a **named constant** instance.
- Meaning and use of a **static initializer block**.

---

## 3. Modeling Relationships and Behavior

### 3.1 Storing Type Matchups

- Each Pokémon type has:
  - A list of types it is **super effective** against.
  - A list for **not very effective**.
  - A list for **no effect**.
- These are **lists of `PokemonType` objects**, not just names or enums.

Conceptually:
java // 
in base class protected ListsuperEffective; protected List notVeryEffective; protected List noEffect;


Each subclass’s `loadRelations()` fills these lists using types from `TypeRegistry`.

---

### 3.2 Behavior Based on State (`effectivenessAgainst`)

- `effectivenessAgainst(PokemonType opponent)` uses the lists above to return a **multiplier**:
  - `2.0` if opponent is in `superEffective`
  - `0.5` if in `notVeryEffective`
  - `0.0` if in `noEffect`
  - `1.0` otherwise
- This is a good example of:
  - **Behavior depending on internal state**.
  - **Encapsulation of rules**: other code doesn’t need to know which list the opponent is in, only the final multiplier.

**Study focus:**
- Be ready to describe how this method uses lists to encode **game rules** in OOP form.

---

## 4. Separation of Concerns: Model vs UI vs Controller

Your app shows a clean separation of **layers**:

### 4.1 Model Layer (Domain Logic)

- All classes in `lab6.type`:
  - `PokemonType` (abstract model)
  - Concrete types (FireType, WaterType, etc.)
  - `TypeRegistry`
- Responsible for:
  - What a type *is*.
  - How it interacts with other types.
  - Storing game rules and data.

### 4.2 UI Layer (Views)

- `TypeSelectorView` (extends `VBox`):
  - Shows the **welcome message** and **grid of type buttons**.
  - Knows **how to display** types (colors, icons, layout).
  - When a button is clicked, it notifies the controller.

- `TypeDetailView` (extends `VBox`):
  - Shows **details for a single type** (name, icon, lists of matchups).
  - Creates nicely styled sections: Super effective, Not very effective, No effect.
  - Buttons for each related type allow **navigation** to that type’s detail view via the controller.

**Study focus:**
- Views work with `PokemonType` objects but **don’t implement game logic** (no matchups rules inside them).

### 4.3 Controller Layer (`AppController`)

- Handles **navigation** and high-level app behavior:
  - Starts with the **type selector view**.
  - When a type is selected, switches to the **detail view** for that type.
- Manages:
  - A JavaFX `Stage` and `Scene`.
  - A root `StackPane` where it swaps views in and out.
  - Background image loading (with error handling).

**Study focus:**
- This is similar to an **MVC**-like split:
  - Model (`lab6.type`)
  - View (`TypeSelectorView`, `TypeDetailView`)
  - Controller (`AppController`)

---

## 5. JavaFX Concepts Touched

(Not the main test topic, but good to recall.)

- Extending layout containers (e.g. `VBox`) to create **custom UI components**.
- Using:
  - `HBox`, `VBox`, `GridPane`, `StackPane`, `FlowPane`.
- Event handling:
  - Implementing `EventHandler<ActionEvent>` to handle button clicks.
  - `btn.setOnAction(this)` or using lambdas.
- Styling:
  - Inline CSS strings to set colors, fonts, borders, background radius.
  - Using `type.getThemeColor()` to dynamically color buttons and panels.

---

## 6. Questions You Should Be Able to Answer

Use these as self-test prompts:

1. **Abstraction & Inheritance**
   - Why is `PokemonType` abstract?
   - What do all concrete type classes inherit from `PokemonType`?

2. **Polymorphism**
   - How can the application treat all types as `PokemonType` while using, for example, `FireType` and `WaterType` underneath?
   - Give an example where a `PokemonType` variable actually holds a specific subtype instance.

3. **Encapsulation**
   - Why are `name`, `imagePath`, and `themeColor` private?
   - How does the rest of the code access those values?

4. **Static Registry**
   - What does `TypeRegistry` provide to the rest of the app?
   - Why are the fields in it `public static final`?

5. **Behavior & Data**
   - How does the program know if a move is 2×, 0.5×, or 0× effective?
   - Where are those relationships stored and how are they used?

6. **Architecture**
   - What are the roles of:
     - `PokemonType` and its subclasses?
     - `TypeSelectorView`?
     - `TypeDetailView`?
     - `AppController`?

If you can answer these clearly, you’ve captured the main OOP ideas of your Lab 6.

---
