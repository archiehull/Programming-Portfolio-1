# Summative Assessment 3 - Repeating Behavious Using Loops

This assessment is summative - which means that you get feedback for completing this, and marks from this work count towards your final mark for this portfolio.

## ToDo List

- [ ] [:key: Demonstrate the ability to declare, access and modify the contents of arrays.](#declaring-arrays)
- [ ] [:key: Demonstrate the ability to iterate over arrays.](#iterating-arrays)
- [ ] [:key: Demonstrate an understanding of why arrays are reference types, what reference type means and the implications of that.](#reference-types)
- [ ] [:key: Demonstrate the ability to how to use a multidimensional array.](#multidimentional-arrays)

- [ ] [:speech_balloon: Express new semantics](#semantics)
- [ ] [:thought_balloon: Reflect on what you have learnt](#reflection)

- [ ] :white_check_mark: Get your work checked off by a feedback engineer

## Declaring Arrays

Arrays can be declared in different ways, one of which involved declaring the array data type, then declaring the size of the array.

```cs
int[] numbers; 
string[] names; 

numbers = new int[10]; 
names = new int[25];
```

If you know what data will be going into your array when you write your code you can also declare your arrays like this:

```cs
int[] numbers = { 10, 20, 15, 3, 99 };
int[] names = { "Matt", "Ross", "Emma", "Camila" };
```

Arrays can be accessed by calling the name of the array, followed by in the index number in square brackets.

```cs
Console.WriteLine(numbers[0]); 
Console.WriteLine(names[2]); 
```

```console
10
Emma
```

You can modify values to elements in an array as you would any other variable.

```cs
numbers[4] = 100; 
names[2] = "Aditi"; 
```

## Iterating Arrays
Using a for loop, the values in an array can be accessed using the iterative value of i.

```cs
int[] numbers;
numbers = new int[9]

for (int i = 0; i < numbers.Length; i++)
{
    Console.WriteLine("Enter the number for index value " + (i));
    numbers[i] = int.Parse(Console.ReadLine());
}
```
## Reference Types

There are two types of memory storage - by reference and by value.

*By Reference* uses pointers to access memory locations that are seperate from where the array is created.

*By Value* uses contiguous memory storage to store array data consecutively in memory.

## Multidimentional Arrays

Multidimensional arrays operate in a similar way to a table or linked lists - in which the index values serve as an axis / column-row value.

Array ( a row of elements ):
```cs
[ ][ ][ ][ ][ ][ ]
```
2-D Array ( a table ):
```cs
[ ][ ][ ][ ][ ][ ]
[ ][ ][ ][ ][ ][ ]
[ ][ ][ ][ ][ ][ ]
[ ][ ][ ][ ][ ][ ]
```

3-D Array ( a cube ) etc...

Multidensional arrays can be called with the following :

```cs
char[,] board = new char[7, 6];
board[0, 0] = 'R';
```


## Semantics

| Word | Synonyms | Meaning |
|---|---|---|
|Array| connected variables | a series of emory locations with uniform data types|
|“contiguous in memory”| adjacent | when data is stored next to each other in memory|
|Element| array variable | a variable in an array |
|Index| array location | the elements in an array |
|Reference type / Managed by reference| referred memory | when an area of memory is allocated to an array, and isn't stored where it's created, but serves more as a pointer|
|Value type / Managed by value| direct memory | memory is allocated directly where it's created |
|For each| index loop | a loop repeating for each index value of the array|
|Out of bounds| off limits| when an array index is accessed out of the declared memory area|

## Reflection

In this section you should reflect upon what you have learnt. This is an important part of the learning process.
- What have you learnt from these exercises?
how to iterate arrays in c#


- How can you apply what you have learnt?
in future programs in c#


- What new features of C# are you now able to use?
arrays and iteration
