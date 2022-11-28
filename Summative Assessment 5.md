# 441101-2223-Summative-5

# To Do

- [ ] [:key: Split a string into several strings using appropriate delimiters.](#splitting-and-extracting-strings)

- [ ] [:key: Extract part of a string (a substring) from a larger string.](#splitting-and-extracting-strings)

- [ ] [:key: Iterate over the characters in a string.](#iterating-strings)

- [ ] [:key: Demonstrate an understanding of why strings are immutable reference types and what the implications of that are.](#understanding-strings)


- [ ] [:speech_balloon: Express new semantics](#semantics)
- [ ] [:thought_balloon: Reflect on what you have learnt](#reflection)

## Splitting and Extracting strings


Using the *".Split"* suffix, spaces can be used to seperate a string of text and extract into an array, where each element is a word.

For example :

```console
User Input :
"Uni of Hull Computer Science"
```
```cs
string input = Console.ReadLine();

string[] separateStrings = input.Split(' ');

for (int i = 0; i < separateStrings.Length; i++) 
{
  Console.WriteLine(separateStrings[i]);
}
```
```console
Console Output:
Uni
of
Hull
Computer Science
```

## Iterating strings

Use the *"Title Case Program"* example, iteration can be used in strings in order to capitalise the first letter of each word in a string using *characterIndex*.

The program uses a for loop to go through each letter of each word in the string and uses the *"char.ToUpper"* function to capatilse the start of each word, the first letter of a word being when *characterIndex = 0* or the character follows a space (" ").

```cs
Console.WriteLine("Title Case Program");
Console.WriteLine("Please Enter The String To Be Converted To Title Case");

string input = Console.ReadLine();

string output = string.Empty;

input = input.ToLower();

for (int characterIndex = 0; characterIndex < input.Length; characterIndex++)
{
if (characterIndex == 0)
  {
  output += char.ToUpper(input[characterIndex]);
  }

else if (input[characterIndex - 1] == ' ')
  {
    output += char.ToUpper(input[characterIndex]);
  }
  
else
  {
    output += input[characterIndex];
  }
}


```

## Understanding strings

Strings are immutable reference types because they are essentially character arrays and cannot be changed. When a string is edited, instead of changing the values within the string, a new string is created and the information from its predecessor is coppied over.

## Semantics

| Word | Synonyms | Meaning |
|---|---|---|
|string|words|a sequence of characters |
|char|character | a letter of the alphabet |
|Concatenate| arrange |the joining of strings |
|Escape Character| control phrase | Character which invokes an alternative interpretation on subsequent characters in a character sequence|
|Immutable|unchangable | fixed |
|Delimiter|boundry |Sequence of one or more characters used to specify a boundary |
|Interpolated String| variable substitution |changing a strings placeholders resulting in the placeholders being replaced with their corresponding values |
|Out of bounds|out of access | accessing an aeeay outside of its|
|Verbatim|identical|directly corresponding |
|null|n/a | void |

## Reflection

In this section you should reflect upon what you have learnt. This is an important part of the learning process.
- What have you learnt from these exercises?
how to use strings in c#


- How can you apply what you have learnt?
in future programs in c#


- What new features of C# are you now able to use?
strings
