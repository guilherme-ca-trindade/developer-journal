# Lab 1 - Introduction to Java
In Lab1.java, create a program of your choosing that meets the following criteria:

## Objectives
8.1. Uses at least two different types of variables✅
8.2. Uses at least one conditional statement✅
8.3. Uses at least one loop✅
8.4. Obtains keyboard input from the user in some way✅
8.5. Prints information to the console✅
8.6. Writes information to a file✅
8.7. Gracefully handles errors using try/catch✅
8.8. Uses a List or array in a meaningful way (perhaps collect multiple user inputs into a List and then iterate over the list to display/store the information)✅
8.9. A function that accepts at least one argument and returns a value is defined and used ✅
NOTE: The ‘main’ function does not count✅
8.10. JavaDoc to document the function(s) you create✅
8.11. Other code comments as appropriate✅

---
## My project
Create a small project based on Dungeons and Dragons and RPG. The code will use 3 attributes, roll the dice D20 and face a challenge (randomized by the D20). 
>In Dnd, we use 6 attributes: Strength, Dexterity, Constitution, Intelligence, Wisdom, and Charisma. The code will use only the first 3 attributes just to be easier. 
The code will run following this:
1. The code have two other functions beside the `main()` function, the `rollDice` to run the D20 with the modifier and `CD` to get the Challeng Difficulty
2. The code will welcome the message and ask the user to type the modifier value from the range of 0 to 5 for the attributes of Strength, Dexterity, Constitution. Using a loop for read the user input for each attribute
3. Try to save the attibrutes and their value assigned by the user to a file `sheet.txt`.
4. Ask the user to type the attribute to roll the dice, with a loop to get a valid response.
5. Then, the `rollDice` function will get the modifier based on the user choice and attribute value, and roll the dice based on that. Showing the result in the output.
6. Finally, it will randomize the CD challenge and compare your roll with the challenge with a If statement, to see if you won or you lost!

---
## Checkpoints
Some importants things to remember and don't forget it. 

## Java Standard and JDK 25
### Java Standard 
In traditional Java, user input is handled using the Scanner class from the java.util package
- ✅ Part of the official Java Standard Library
- ✅ Works in all Java environments
- ❌ Slightly verbose for beginners
`import java.util.Scanner;`
`Scanner scanner = new Scanner(System.in);`
`String input = scanner.nextLine();`

### JDK 25
- ✅ Easier syntax for beginners
- ✅ Often used in teaching tools or custom setups
- ❌ Not part of the official Java Standard Library
- ❌ Requires specific environment that supports IO
`IO.println("Enter your name:");`
`String name = IO.readln();`

>- If you're using standard Java, you must use Scanner.
>- If you're using JDK 25 with IO support, you can use IO.readln() and IO.println().
>- Mixing both (Scanner and IO) in the same program is not recommended unless you're sure both are supported.
### Static vs Dynamic Typing
Java is statically typed, meaning that programers must declare in code the type of any variables and parameters. This is in contrast to a dynamically typed language like Python where a variable’s type is determined at runtime and need not be made explicit in code.
`<type> <variablename> = <value>;`
You can use the var keyword in place of a variable’s type for variables that are declared…
- inside a function body
- with initialization
`var x = 1;    // x will have type int`
`var s = "Hi"; // s will have type String`

### File handling in Java
- `FileWriter`: A class used to write text data to a file, character by character.
- File name ("sheet.txt"): The name of the file being created or overwritten. If the file doesn’t exist, Java creates it.
- `.write()` method: Adds text to the file. You can use \n to insert line breaks.
- `.close()` method: Always close the file after writing to ensure data is saved and resources are released.
- `try`/`catch` block: Required to handle potential errors like permission issues or missing directories.
- `IOException`: The type of error that might occur when writing to a file (e.g., disk full, file locked)

### parseInt() and convert the user input to Integer
It is used to read a number from the user and convert it into an integer. Here's how it works, step by step:
- IO.readln()
Reads a line of text input from the user. The result is a String, even if the user types a number.
- Integer.parseInt(...)
Converts that String into an int. If the user types "5", this turns it into the number 5.
Java doesn’t automatically convert text input into numbers. So when you ask the user to type a number, you have to:
- Read it as text (String)
- Convert it to a number (int)
If the user types something that isn’t a number (like "hello"), Integer.parseInt() will throw an error. That’s why we use a try/catch block to handle it safely.
