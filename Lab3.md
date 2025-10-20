# TicTacToe

## Overview
- This lab was made with Francisco and to create a Tic Tac Toe using Java.
Francisco helped me a lot to understand or to strength some Java concepts, giving a lot of support to make everything working. Almost working like a Senior and Junior LOL.
- I get focused on the console and the JavaFX, and Francisco on the board and getting all together in the main. The hardest part was to use JavaFX and connecting to our project,
    and this took more time than expected. Requesting support from ChatGPT (study mode), professor's explanation and Francisco's small adjusts, and some deeper concepts must be
    revisit precisely again for me in the future (like interfaces, packages and modules).

- I had more doubt writing the code, but instead asking ChatGPT, I ask for help to Francisco, giving way more understanding about the language and major diferences between Java and Python.
  Due to that, I realized that I have more knowledge reading Java scripts rather than writing from the scratch. Even though I have the programming concepts fixed on my mind, when comes to
  write, a blank space can appear often and must be revisited.

  ### The code
  The program is working perfectly and can be played using the JavaFX GUI rather than the console. I think that the code could be better shaped, reducing the size of the Main or creating other
  class and functions. Otherwise, I really love to create this project and the result.

  ## AI Statement
  I did not use other AI beside the ChatGPT (in the study mode), allowed for the professor during this lab. ChatGPT helps (sometimes not) especially with the JavaFX.




-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
## Setup
- **JDK:** 25  
- **Framework:** JavaFX 23 (via Maven)  
- **Build Tool:** Maven  

### Maven Configuration
```xml
<dependencies>
  <dependency>
    <groupId>org.openjfx</groupId>
    <artifactId>javafx-controls</artifactId>
    <version>23.0.1</version>
  </dependency>
  <dependency>
    <groupId>org.openjfx</groupId>
    <artifactId>javafx-fxml</artifactId>
    <version>23.0.1</version>
  </dependency>
</dependencies>
```

Run with:
```bash
mvn javafx:run
```

---

## Layout
- **Root:** `VBox`
  - `Label` (turn indicator)
  - `GridPane` (3×3 board)
  - `Button` ("New Game" reset)

---

## Core Logic
- `handleMove()` updates the board, switches players, and checks win/draw.  
- Button colors: **Red (X)** and **Blue (O)**.  
- Turn label updates dynamically.

---

## Reset Function
```java
private void resetBoard(GridPane grid) {
    game.resetGame();
    for (Node node : grid.getChildren()) {
        if (node instanceof Button btn) {
            btn.setText("");
            btn.setDisable(false);
            btn.setTextFill(Color.BLACK);
            btn.setBackground(Background.EMPTY);
        }
    }
    currentPlayer = Play.PX;
    turnLabel.setText("[Player X's turn]");
}
```

---


## Common Fixes
- **Duplicate children:** avoid adding same node twice.  
- **Grid disappearing:** don’t recreate the layout on reset.  
- **Old styles persisting:** reset text color and background.
