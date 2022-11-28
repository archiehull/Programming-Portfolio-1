# 441101-2223-Summative-6

:key: Give examples of when you have called a method that already exists.

:key: Demonstrate how to write and call a method, and how to pass data into a method and get data out of a method.

:key: Demonstrate how to use methods to increase readability and reduce scope.

:key: Demonstrate the use of optional parameters and method overloading.

## Calling and Passing Methods

```cs
void SayHello()
{
    Console.WriteLine("Hello, World!");
}

void SayHelloWithName(string pName)
{
    Console.WriteLine($"Hello, {pName}");
}

string GetName()
{
    Console.WriteLine("What is your name?");
    string name = Console.ReadLine();
    return name;
}

string name = GetName()

SayHelloWithName(name)

```

```console
What is your name?
archie
Hello, archie
```


## Using Methods to Increase Readability and Reduce Scope

## Optional Parameters and Method Overloading

## Semantics
 
| Word | Synonyms | Meaning |
|---|---|---|
|Method Signature| | |
|Parameter| | |
|Argument| | |
|Return type| | |
|Method Call| | |
|Method Scope| | |
|Overloaded Method| | |
|Optional Parameter| | |
|Refactor| | |
