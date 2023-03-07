Key Concept - To be able to appropriately reuse code using inheritance

From character class : healthpoints and energy points are created and have get and set conditions created
```cs

public int healthPoints
    {
        get
        { return _healthPoints; }
        set
        {
            if (value < maxHealth) { _healthPoints = value; }
            else { _healthPoints = maxHealth; }
        }
    }
    public int energyPoints
    {
        get { return _energyPoints; }
        protected set
        {
            if (value < maxEnergy) { _energyPoints = value; }
            else { _energyPoints = maxEnergy; }
        }
    }
```

these variables are reused and inherited in the child classes, such as in ranger, where the values are modified within the child class.

```cs
public Ranger(string Name) : base(Name)
    {
        maxHealth = 10;
        maxEnergy = 8;
        numberOfArrows = 10;
        firedArrows = 0;
    }

    public void CollectArrows()
    {
        numberOfArrows += firedArrows;
        firedArrows = 0;
    }

    public void FireArrows(Character target)
    {
        if (numberOfArrows > 0 && energyPoints >= 1 && !isKnockedOut)
        {
            energyPoints -= 1; 
            numberOfArrows--;
            firedArrows++;
            Console.WriteLine($"{Name} the ranger shot an arrow at {target.Name}.");
            target.healthPoints -= 1;
        }
    }
    ```


Key Concept - To be able to call a base constructor from a child constructor
ranger is called from charater

```cs
public class Ranger : Character
{
    public Ranger(string Name) : base(Name)
    
```


Key Concept - To be understand access modifiers in inheritance hierarchies

Use of "protected set" means its only accessable within the class and its child classes. Public makes it accessable from all classes, private keeps it contained and accessable within the class.

```cs
    public int energyPoints
    {
        get { return _energyPoints; }
        protected set
        {
            if (value < maxEnergy) { _energyPoints = value; }
            else { _energyPoints = maxEnergy; }
        }
    }
 ```

Key Concept - Demonstrate the above skills by completing the challenge exercise

```cs

public class Character
{
    public int _healthPoints;
    public int _energyPoints;
    public string Name { get; private set; }
    public int maxHealth;
    public int maxEnergy;
    public int numberOfArrows { get; protected set; }
    public int firedArrows { get; protected set; }

    public int healthPoints
    {
        get
        { return _healthPoints; }
        set
        {
            if (value < maxHealth) { _healthPoints = value; }
            else { _healthPoints = maxHealth; }
        }
    }
    public int energyPoints
    {
        get { return _energyPoints; }
        protected set
        {
            if (value < maxEnergy) { _energyPoints = value; }
            else { _energyPoints = maxEnergy; }
        }
    }

    public Character(string Name)
    {
        this.Name = Name;
    }

    public bool isKnockedOut { get { return healthPoints <= 0; } }

    public void Rest()
    {
        if (!isKnockedOut)
        {
            energyPoints = maxEnergy;
            healthPoints = maxHealth;
        }
    }
}

public class Ranger : Character
{
    public Ranger(string Name) : base(Name)
    {
        maxHealth = 10;
        maxEnergy = 8;
        numberOfArrows = 10;
        firedArrows = 0;
    }

    public void CollectArrows()
    {
        numberOfArrows += firedArrows;
        firedArrows = 0;
    }

    public void FireArrows(Character target)
    {
        if (numberOfArrows > 0 && energyPoints >= 1 && !isKnockedOut)
        {
            energyPoints -= 1; 
            numberOfArrows--;
            firedArrows++;
            Console.WriteLine($"{Name} the ranger shot an arrow at {target.Name}.");
            target.healthPoints -= 1;
        }
    }
}

public class Barbarian : Character
{
    public Barbarian(string Name) : base(Name)
    {
        maxHealth = 18;
        maxEnergy = 12;
    }

    public void SwingAxe(Character target)
    {
        if (energyPoints >= 3 && !isKnockedOut)
        {
            Console.WriteLine($"{Name} the barbarian swung his mighty axe at {target.Name}.");
            target.healthPoints -= 3;
        }
    }
}

public class Mage : Character
{
    public Mage(string Name) : base(Name)
    {
        maxHealth = 8;
        maxEnergy = 8;
    }

    public void ThrowFireball(Character target)
    {
        if (energyPoints >= 2 && !isKnockedOut)
        {
            Console.WriteLine($"{Name} the mage threw a fireball at {target.Name}.");
            target.healthPoints -= 2;
        }
    }

    public void Heal(Character target)
    {
        if (energyPoints >= 1 && !isKnockedOut)
        {
            energyPoints -= 1;
            target.healthPoints += 5;
        }
    }
}

public class Knight : Character
{
    public Knight(string Name) : base(Name)
    {
        maxHealth = 12;
        maxEnergy = 12;
    }

    public void ShieldBash(Character target)
    {
        if (energyPoints >= 2 && !isKnockedOut)
        {
            Console.WriteLine($"{Name} the knght bashed {target.Name} with its shield.");
            target.healthPoints -= 2;
        }
    }

    public void SwingSword(Character target)
    {
        if (energyPoints >= 3 && !isKnockedOut)
        {
            energyPoints -= 3;
            Console.WriteLine($"{Name} the knght swung its sword at {target.Name}.");
            target.healthPoints -= 4;
        }
    }
}

/////////////////

Console.WriteLine("Hello, Mini Heroes Quest!");

Ranger ranger = new Ranger("John");
Barbarian barbarian = new Barbarian("Susan");
Mage mage = new Mage("Richard");


Console.WriteLine($"{ranger.Name} the ranger joined the party!");
Console.WriteLine($"{barbarian.Name} the barbarian joined the party!");
Console.WriteLine($"{mage.Name} the mage joined the party!");

ranger.FireArrows(barbarian);
barbarian.SwingAxe(mage);
mage.ThrowFireball(ranger);
ranger.FireArrows(mage);
mage.Heal(barbarian);
ranger.FireArrows(barbarian);
ranger.FireArrows(barbarian);
ranger.FireArrows(barbarian);
ranger.FireArrows(barbarian);
ranger.FireArrows(barbarian);
ranger.FireArrows(barbarian);
ranger.FireArrows(barbarian);
ranger.FireArrows(barbarian);
ranger.FireArrows(barbarian);
ranger.FireArrows(barbarian); // The ranger has fired all arrows
ranger.CollectArrows(); // The ranger collects all the fired arrows

Console.WriteLine($"{ranger.Name} has {ranger.numberOfArrows} arrows left.");
Console.WriteLine($"{barbarian.Name} has {barbarian.healthPoints} health points left.");
Console.WriteLine($"{mage.Name} has {mage.energyPoints} energy points left.");

ranger.Rest();
barbarian.Rest();
mage.Rest();

Console.WriteLine($"{ranger.Name}, {barbarian.Name}, and {mage.Name} all took a rest!");

Knight knight = new Knight("Niel");

knight.SwingSword(mage);

Console.ReadLine();



```


## Semantics 

| Word | definition|
|---|---|
|inheritance		|used by classes that take information from other related classes|
|"is-a" relationship|		used to describe what the relationship is between the child and parent classes.|
|parent class	|the main constructor and the methods that will be used be the children|
|derived class	|inherits from the parent class|
|protected		|can only be accessed by that class or a child of that class|
|dependency		|code that is required by the class for it to function|
|diamond of death|when a class has 2 or more parents|


	



## Reflection

In this section you should reflect upon what you have learnt. This is an important part of the learning process.
- What have you learnt from these exercises?

how to use classes in c#


- How can you apply what you have learnt?

in future programs in c#


- What new features of C# are you now able to use?

classes
