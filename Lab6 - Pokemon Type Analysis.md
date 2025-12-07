
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
