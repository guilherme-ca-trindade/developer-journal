# Summary of "Intro to JavaFX" Lecture

## Main Topics Covered

### 1. **What is JavaFX?**
- Modern GUI framework for Java (replacement for Swing)
- Rich set of UI controls, styling via CSS, animation support
- Uses GPU acceleration for better performance

### 2. **Setup and Installation**
- Not included in JDK 11+ (must be added as dependency)
- **Maven dependency**:
```xml
<dependency>
    <groupId>org.openjfx</groupId>
    <artifactId>javafx-controls</artifactId>
    <version>23</version>
</dependency>
```
- Requires **module-info.java** for modular projects:
```java
module myapp {
    requires javafx.controls;
    exports mypackage;
}
```

### 3. **JavaFX Application Structure**
- **Application** class: Entry point for JavaFX apps
- **Stage**: Main window (has title, borders, buttons)
- **Scene**: Container for UI components
- **Scene Graph**: Tree of **Node** objects

```java
public class MyApp extends Application {
    @Override
    public void start(Stage stage) {
        // Setup UI here
    }
    
    public static void main(String[] args) {
        launch(args);
    }
}
```

### 4. **Node Hierarchy**
```
Node (abstract)
├── Parent (abstract)
│   ├── Group (logical grouping)
│   └── Region (stylable with CSS)
│       ├── Pane (layout managers)
│       └── Control (interactive UI)
└── Shape (drawable elements)
    ├── Rectangle, Circle, Ellipse, Line, etc.
    └── Text
```

### 5. **Layout Panes (Containers)**
| Pane | Arrangement |
|------|-------------|
| **VBox** | Vertical stacking |
| **HBox** | Horizontal stacking |
| **StackPane** | Layers children (top to bottom) |
| **BorderPane** | Top, bottom, left, right, center |
| **GridPane** | Grid/table layout |
| **FlowPane** | Wraps like text |
| **AnchorPane** | Anchored to edges |

**Adding nodes to panes:**
```java
VBox vbox = new VBox(child1, child2);           // Constructor
vbox.getChildren().add(child3);                 // Add single
vbox.getChildren().addAll(child4, child5);     // Add multiple
```

### 6. **Shapes and Text**
```java
// Creating shapes
Ellipse ellipse = new Ellipse(110, 70);
ellipse.setFill(Color.BLACK);
ellipse.setStroke(Color.HOTPINK);

// Creating text
Text text = new Text("Hello JavaFX");
text.setFont(new Font("Arial Bold", 24));
text.setFill(Color.WHITE);

// Adding to container
StackPane pane = new StackPane();
pane.getChildren().addAll(ellipse, text);
```

### 7. **Colors and Paint**
```java
Color.LIGHTBLUE;                // Named color
Color.rgb(52, 5, 70);           // RGB values (0-255)
Color.web("#340546");           // Hex code
Color.gray(0.5);                // Grayscale (0-1)

// Other Paint types
LinearGradient gradient = new LinearGradient(...);
ImagePattern pattern = new ImagePattern(...);
```

### 8. **Effects and Animation**
**Effects:**
```java
DropShadow shadow = new DropShadow(5, 0, 0, Color.WHITE);
text.setEffect(shadow);

Reflection reflection = new Reflection();
reflection.setFraction(0.2);
ellipse.setEffect(reflection);
```

**Animations (Transitions):**
```java
ScaleTransition scale = new ScaleTransition(Duration.seconds(0.1), node);
scale.setToX(1.2);
scale.setToY(1.2);
scale.setAutoReverse(true);
scale.setCycleCount(2);
scale.playFromStart();
```

### 9. **Event Handling**
**Using EventHandler interface:**
```java
public class ClickHandler implements EventHandler<MouseEvent> {
    @Override
    public void handle(MouseEvent event) {
        System.out.println("Clicked at: " + event.getX() + "," + event.getY());
    }
}

// Attaching handler
Button button = new Button("Click me!");
button.setOnMouseClicked(new ClickHandler());
```

**Lambda alternative:**
```java
button.setOnMouseClicked(event -> {
    System.out.println("Button clicked!");
});
```

### 10. **Controls (UI Components)**
- **Labelled**: Button, CheckBox, Label, RadioButton
- **Text Input**: TextField, TextArea, PasswordField
- **Other**: ProgressBar, Slider, ListView, ComboBox

**Example:**
```java
Button btn = new Button("Submit");
TextField field = new TextField();
CheckBox check = new CheckBox("Agree to terms");
Slider slider = new Slider(0, 100, 50);
```

### 11. **Coordinate System**
- Origin (0,0) at **top-left** corner
- X increases to the **right**
- Y increases **downward**

```
(0,0) ────────────────► X
  │
  │
  ▼
  Y
```

### 12. **Padding and Spacing**
```java
VBox vbox = new VBox();
vbox.setPadding(new Insets(10));           // All sides: 10px
vbox.setPadding(new Insets(10, 50, 50, 50)); // Top, Right, Bottom, Left
vbox.setSpacing(5);                        // Space between children
```

---

## Key Code Example: Complete App
```java
import javafx.application.Application;
import javafx.scene.Scene;
import javafx.scene.control.Button;
import javafx.scene.control.Label;
import javafx.scene.layout.VBox;
import javafx.stage.Stage;

public class SimpleApp extends Application {
    @Override
    public void start(Stage stage) {
        Label label = new Label("Welcome to JavaFX!");
        Button button = new Button("Click me");
        
        button.setOnAction(e -> {
            label.setText("Button was clicked!");
        });
        
        VBox root = new VBox(10, label, button);
        root.setPadding(new Insets(20));
        
        Scene scene = new Scene(root, 300, 200);
        stage.setTitle("My JavaFX App");
        stage.setScene(scene);
        stage.show();
    }
    
    public static void main(String[] args) {
        launch(args);
    }
}
```

---

## Important Concepts to Remember
1. **JavaFX requires manual setup** (dependency/module)
2. **Application → Stage → Scene → Node** hierarchy
3. **Panes manage layout**, not absolute positioning
4. **EventHandler** interface for responding to user actions
5. **CSS styling** available for all nodes
6. **Animations** via Transition classes
7. **Coordinate system** starts at top-left

---

## Resources
- [JavaFX Layout Examples](https://github.com/Apress/learn-javafx17)
- [Official Documentation](https://openjfx.io/)
- [JavaFX Controls Gallery](https://fxdocs.github.io/docs/html5/)

---

This lecture provides the foundation for building modern, interactive desktop applications with JavaFX, covering everything from basic setup to advanced features like animation and event handling.
