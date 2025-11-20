# Introduction to Java

## What you already know
	- Programming languages are formal languages that can be understood by both humans and computers
		○ Teams of people must be able to express complex computations, and understand and update the code they created
		○ Interpreters/compilers must be able to convert code files into the very simple instructions of machine language

	### - Most programming languages are 'equivalent' in the sense that they could be used to write any and all software, such languages have:
	1. Ability to retrieve data (Input)
	2. Ability to store data (Output)
	3. Ability to perform arithmetic (Increment, Multiply, etc.)
	4. Conditional Execution (If/Else)
	5. Repetition (Loops, Recursive functions)

## Language types
### Interpreted 
	- Code files are executed directly via an interpreter program that converts code into machine code at run time
	- Can only be executed on platforms on which the interpreter can run.
	- E.g. JavaScript, PHP, Python, Ruby

### Compiled
	- A compiler program converts code files into executable files on target platform
	- Executable files are executed directly
	- E.g. C, C++, Rust, Swift

### Hybrid
	- A compiler program converts code files into an intermediate bytecode
	- Bytecode is executed by a virtual machine, which is effectively a bytecode interpreter
	- Can be executed on any platform supported by the virtual machine.
	- E.g. C#, Java, Erlang
> Java need a virtual machine to have this bytecode interpreted, often called JVM. Using Java this step could pass hidden by us, but Java is a hybrid language


## Java 
	- The Java programming language is a hybrid language
	- Compiler converts Java code files into Java bytecode
	- Java Virtual Machine (JVM) runs Java bytecode files
	- JVM is supported in a wide range of hardware platforms

## Java vs JavaScript
	- Java and JavaScript are not the same language
	- Similar names due to 1990s marketing silliness
	- Be careful when searching information about either language

## Java Development Kit (JDK)
	- To run Java programs, you must have the JVM installed
	- To create Java programs, you will need the JDK
		○ JVM (Java)
		○ Compiler (Javac)
		○ REPL shell (Jshell)
	- Can install multiple JDKs on one device
		○ Be careful about which JDK is being used when creating a Java program

	- The Java language is a programming language specification
	- Oracle owns the specification
	- Many vendors produce implementations of the JDK:
		○ Amazon (Corretto)
		○ Microsoft (Microsoft Build of OpenJDK)
		○ Oracle (OracleJDK, OpenJDK)
	- Different implementations have different licensing and performance

	- Java language specification is updated regularly with new features
	- Certain versions are marked as Long-Term Support (LTS)
		○ These versions receive regular security updates and patches
		○ Usually best to an LTS version for production development

## Java Syntax
	- Recall: a programming language's syntax is its 'grammatical rules'
	- Syntax errors occur when you break those rules
		○ In a compile language, syntax errors are detected by the compiler and are sometimes called compile-time errors

### Static and dynamic languages
>You must declare the type of variables in a static language. Different than a dynamic language, like Python, that define the type during the runtime process. However, in a static language, like Java, it'll say that happen a compile-time error.
>You can use var (for variable) if you don't to think or know the type of this variable, and the compiler will interpret the type of the variable instead of requiring you to declare it.

### Types
Primitive types:
Boolean (true or false)
Byte 8-bit int
Short 16-bit int
Int 32-bit int
Long 64-bit int
Float 32-float number
Double 64- float number
Char a single Unicode character

### Object types (Classes):
- Anything that is not one of the 8 primitive types is an object type
