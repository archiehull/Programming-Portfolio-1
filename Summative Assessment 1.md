# Summative Assessment 1 - Using Visual Studio - Variables, types, casting and parsing

This assessment is summative - which means that you get feedback for completing this, and marks from this work count towards your final mark for this portfolio.

## ToDo List

- [ ] [:key: Can describe the structure of a Visual Studio project](#visual-studio)
- [ ] [:key: Can declare variables with a type, assign a value to a variable and identify what that type means](#declaring-a-variable)
- [ ] [:key: Can cast one type to another and identify when and why this is required](#casting-a-value)
- [ ] [:key: Can parse a string to a variable of another type and identify when and why this is required](#parsing-a-string)
- [ ] [:speech_balloon: Express new semantics](#semantics)
- [ ] [:thought_balloon: Reflect on what you have learnt](#reflection)
- [ ] [:question: Request feedback (optional)](#requesting-feedback)
- [ ] :white_check_mark: Get your work checked off by a feedback engineer

## Visual Studio

Here demonstrate that you understand the structure of a visual studio project, and the different files it uses.

--------------------------

The structure of a VS project begins by selecting a template (if desired). The template will determine which programming language(s) will be used within the project and which platforms the program is intended to run on. Following template selection, the file cam be named and the framework type can be selected (typically .NET 5 or 6) - then the coding can begin.
A folder will be created containing a *'.sln'* file, and a subfolder containing the initial project name which, depending on what language you're coding in, will be a *'.##proj'* file (i.e. *'.csproj'*, *'.vcproj'*, etc.) - and a *'.##'* (i.e. *'.cs'*) .

The .proj file cointains intructions on how to compile the code contained in the .## file.
The .sln file contains plaintext which groups all the project files within the folder together.

## Declaring a variable

Here demonstrate your understanding of variables, types and assignments.

--------------------------
In the code below - the prefixes *'int'* and *'float'* are used to create variables and assign them to the required data type.
```cs
int integer = 3;
float taolf = 7.5f;

Console.WriteLine(integer);
Console.WriteLine(taolf);
```


## Casting a value

Here demonstrate that you understand how to cast one type to another, and when and why you should do that.

--------------------------
The code below is an example of implicit casting, which is the casting of a smaller size type to a larger size type - which can be done automatically. Explicit casting occurs when casting from larger to smaller and must be done through the use of manual conversion.
```cs
int integer = 3;
float taolf = integer;

Console.WriteLine(integer);
Console.WriteLine(taolf);
```


## Parsing a string

Here demonstrate that you understand how to parse a string to another type, and when and why you should do that.

--------------------------
The code below shows an example of Parsing, which is a method used to convert data types. It is commonanly used in a similar fasion to this example, where it's converting a string, entered by the user, to an integer, in order to make the value enter mathmatically usable and have it assigned to a variable.

```cs
Console.WriteLine("Enter a number :");

int number = int.Parse(Console.ReadLine());

int newnumber = number * 2;

Console.WriteLine("Your number * 2 is : " + newnumber);
```

## Requesting Feedback

This section is optional, but encouraged. Feedback is crucial to the learning process. If you have any questions about what you have learnt this week record them here for your demonstrator to answer. **Replace** the bullet points below with any questions you might have.
- Why are we here?
- What is the meaning of life?

## Semantics

In order to talk about programming we need to establish a set of core terminology, or "semantics". In this context "semantics" means the words we use to talk about programming. This is different to Syntax, which is what we type to tell the computer what we want it do to. It is important that when we use words that have
a special meaning in the context of programming we share a common understanding.

Complete this table of semantics with your understanding of what these terms mean:

| Word | Synonyms | Meaning |
|---|---|---|
|Variable|container|a location in which data is stored|
|Identifier| Name | the user-defined name of a program element. It can be a namespace, class, method, variable or interface.|
|Type|group| how to data can be used and interpreated|
|Cast|convert|changing from one data type to another |
|Parse|change|converting from a string to another data type|
|Integer|digit|whole number |
|Floating Point|Real| decimal number|
|String|word|a series of connected characters |

## Reflection
In this section you should reflect upon what you have learnt. This is an important part of the learning process.
- What have you learnt from these exercises?

how to use conversion in c#
- How can you apply what you have learnt?

when using data types in other programs, i will have a better understanding
- What new features of C# are you now able to use?

casting and parsing
