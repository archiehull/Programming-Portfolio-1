:key: Demonstrate and understanding of the implications of passing values by reference using the in, our and ref keywords.

:key: Demonstrate and understand the implications of passing reference types, such as arrays, by value and by reference.

:key: Demonstrate how to write less code by reusing methods.

:key: Demonstrate how to use delegates.

## Passing by reference

```cs
int x = 10;
Multiplication(ref x);
```
ref - 
The value is read only and cannot be changed at any point. It is effectively copying the value into where it is being called and therefore does not affect the original variable.

in - 
Can't be modified (assign to) a variable inside a function, but can be called by methods. 
Essentially the variable is read-only inside the function body (but the object is still modifiable internally via its interface).

out-
Exactly like ref but you don't need to initialize the variable before calling the function and do need to assign a value to the out parameter before returning from the function.

## Ref vs Val
Passing by value would mean that any changes made to the number passed into the function/method would change the actual value of the passed data, whereas passing by reference would create a copy of the passed data, and leave the original variable the same.

So passing an elemant in an array by value would change that elemant in the array which would be used at an ATM for example, where when you can see the amount of money you have on screen and money is withdrawn, it will change the value on screen and in your account.
If you wanted to view how much interest you would earn from the money in your account after 3 years, you would pass by reference, as you dont want to change the amount of money in your bank, you just want to use that value in a calculation.

## Semantics

| Word | Synonyms | Meaning |
|---|---|---|
|Pass by reference| | |
|Reference type| | |
|Delegate| | |
|in| | |
|out| | |
|ref| | |
|The DRY principle| | |
|The WET principle| | |
