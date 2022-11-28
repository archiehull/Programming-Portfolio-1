# Summative Assessment 3 - Repeating Behavious Using Loops

This assessment is summative - which means that you get feedback for completing this, and marks from this work count towards your final mark for this portfolio.

## ToDo List

- [ ] [:key: Can describe with examples how a while loop and a do-while loop work, and the difference between them](#do-while-and-while-loops)
- [ ] [:key: Can describe with examples what the break and continue keywords do](#break-and-continue)
- [ ] [:key: Can describe with examples what a nested loop is](#nested-loops)
- [ ] [:speech_balloon: Express new semantics](#semantics)
- [ ] [:thought_balloon: Reflect on what you have learnt](#reflection)
- [ ] [:question: Request feedback (optional)](#requesting-feedback)
- [ ] :white_check_mark: Get your work checked off by a feedback engineer

## Do While and While Loops

The do while loop executes the content of the loop once before checking the condition of the while.
```cs
i =0
do {
        Console.WriteLine("Hello World!")
        i++
    } while(i<2);
```
Whereas a while loop will check the condition first before executing the content.
```cs
i =0
while(i<2) {
        Console.WriteLine("Hello World!")
        i++
    }
```


## Break and Continue

*Break* will exit the loop completely, *Continue* will just skip the current iteration.

The break will cause the loop to exit on the first iteration - DoSomeThingWith will never be executed.

```cs
for (int i = 0; i < 10; i++) {
    if (i == 0) {
        break;
    }

    DoSomeThingWith(i);
}
```

The continue with skip the first iteration, so wont execute *DoSomeThingWith(i)* the first time round - but will for i=1,9.

```cs
for (int i = 0; i < 10; i++) {
    if(i == 0) {
        continue;
    }

    DoSomeThingWith(i);
}
```

## Nested Loops

A nested loop is a loop within a loop, and can be completed using an if loop, while loop or a do while loop.

This is an example of a nested while loop.

```cs
while(condition) {
   while(condition) {
      statement(s);
   }
   statement(s);
}
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
|Loop| cycle| a block of repeating code |
|Initialisation Statements| activation statement| the statement that dictates whether a loop will start or not |
|Condition statements|parameter checking statement | a set of rules that need to return the required output|
|Iterator statements| recursive statement | the statement that dictates what gets modified with each iteration |
|Increment expression| increase factor statement | adds 1 to their operand|
|Decrement expression| decrease factor statement | subtracts 1 to from their operand|
|Prefix| before | the code before a loop / statement |
|Postfix| after | the code after a loop / statement  |


## Reflection
In this section you should reflect upon what you have learnt. This is an important part of the learning process.
- What have you learnt from these exercises?

how to use break and continue and their differences

- How can you apply what you have learnt?

in future conding projects

- What new features of C# are you now able to use?

break & continue
