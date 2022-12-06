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
Will operate as a pointer to the area of memory that the variable uses to store its data and change the data accordingly.
The argument for a ref parameter must be definitely assigned. The called method may reassign that parameter.

```cs
readonly struct VeryLarge
{
    public readonly long Value1;   
    public readonly long Value2;

    public long Compute() { }
    // etc
}

void Process(in VeryLarge value) { }
```

in - 
Can't be modified (assign to) a variable inside a function, but can be called by methods. 
Essentially the variable is read-only inside the function body (but the object is still modifiable internally via its interface).
The argument for an in parameter must be definitely assigned. The called method can't reassign that parameter.

```cs
int initializeInMethod;
OutArgExample(out initializeInMethod);
Console.WriteLine(initializeInMethod);     // value is now 44

void OutArgExample(out int number)
{
    number = 44;
}
```

out-
Exactly like ref but you don't need to initialize the variable before calling the function and do need to assign a value to the out parameter before returning from the function.
The argument for an out parameter needn't be definitely assigned. The called method must assign the parameter.


## Ref vs Val in arrays
Passing by reference would mean that any changes made to the number passed into the function/method would change the actual value of the referenced data, whereas passing by value would create a copy of the passed data, and leave the original variable the same.

So passing an elemant in an array by reference would change that elemant in the array which would be used at an ATM for example, where when you can see the amount of money you have on screen and money is withdrawn, it will change the value on screen and in your account.
If you wanted to view how much interest you would earn from the money in your account after 3 years, you would pass by value, as you dont want to change the amount of money in your bank, you just want to use that value in a calculation.

## Reusing methods

If I have written a piece of code that requires the user to enter unsorted data into multiple arrays and for that data to be sorted - instead of having each array be manually sorted within to tcode and have a lot of repetition, I can write a method and call it multiple teams, for example this bubble sorting method.

```cs
static void bubbleSort(int[] arr)
    {
        int n = arr.Length;
        for (int i = 0; i < n - 1; i++)
            for (int j = 0; j < n - i - 1; j++)
                if (arr[j] > arr[j + 1]) {
                    // swap temp and arr[i]
                    int temp = arr[j];
                    arr[j] = arr[j + 1];
                    arr[j + 1] = temp;
                }
    }
 ```

## Delegates
Delegates are used to pass methods as parameters

```cs
public delegate void MyDelegate(string msg); // declare a delegate

// set target method
MyDelegate del = new MyDelegate(MethodA);

// target method
static void MethodA(string message)
{
    Console.WriteLine(message);
}
```

After setting a target method, a delegate can be invoked using the Invoke() method or using the () operator.

```cs
del.Invoke("Hello World!");
// or 
del("Hello World!");
```



## Semantics

| Word | Synonyms | Meaning |
|---|---|---|
|Pass by reference| pointer | to change redirect the method to the original memory address where it can be modified |
|Reference type| call type| the way in which data is called in a method or function|
|Delegate|redirecter | Passing a method as a parameter|
|in| read only| must be definitely assigned. The called method can't reassign that parameter.|
|out| unsigned|needn't be definitely assigned. The called method must assign the parameter. |
|ref| reference| must be definitely assigned. The called method many reassign that parameter.|
|The DRY principle| shush| dont repeat yourself|
|The WET principle| waffle|  write every time|
