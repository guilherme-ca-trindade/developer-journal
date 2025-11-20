# Lecture 3 - Implementing Classes

## Before we get to OOP…

## Data
	- What kinds of things need to be modelled/simulated?
	- Do built-in types model those things well?
	- Would it be nice to have a certain type available in the language to represent certain data? (e.g. Point, Person, BankTransaction, etc.)
## Operations
	- What operations need to be performed on the program's data?
	- Is it more natural to think of those operations as…
		○ Messages passed to / requests made of the data
			§ Person.getAge( )
		○ Operations to which data is passed
			§ calculateAge(person)

## To represent data…
## Consider…
	### Enumerations (enums)
		○ A way to represent types that can have one of pre-defined set of values
	### Records
		○ A way to represent types that consist of multiple parts

## Enumerations
	- Sometimes a type can be only one of a limited…

## Records
	- Sometimes you just want a way to represent a multi-part value
	- E.g. Person with name and age, Rectangle with x, y, width and length.
	- Java's record syntax (finalized in version 16) provides a concise way to define such type
