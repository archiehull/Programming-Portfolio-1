Key Concept - Be able to override the existing ToString method

As seen in Circle Class
```cs
public override string ToString()
        {
            return $"Circle (ID: {ID}, Colour: {Colour}, Radius: {_radius})";
        }
```

Key Concept - Be able to write virtual methods in a parent class and override those methods in a child class
As seen in Shape and Circle class
```cs
 public virtual double Area()
        {
            throw new NotImplementedException();
        }
```
```cs
public override double Area()
        {
            return Math.PI * _radius * _radius;
        }
```

Key Concept - Be able to invoke child specific behaviour from a reference to a parent class
As seen in Circle and Rectrangle

Key Concept - Demonstrate the above skills by completing the challenge exercise

Shapes
```cs
namespace Shapes
{
    public enum Colour { Red, Green, Blue };

    internal class Shape
    {
        public string Colour { get; set; }

        public int ID { get; private set; }

        private static int _nextID = 1;

        public Shape(string colour)
        {
            Colour = colour;
            ID = _nextID;
            _nextID++;
        }

        public virtual double Area()
        {
            throw new NotImplementedException();
        }

        public virtual double Perimeter()
        {
            throw new NotImplementedException();
        }
    }
}

```
Shape Manager
```cs
namespace Shapes
{
    internal class ShapeManager
    {
        private List<Shape> _shapes;

        public ShapeManager()
        {
            _shapes = new List<Shape>();
        }

        public void AddShape(Shape shape)
        {
            if (!_shapes.Contains(shape))
            {
                _shapes.Add(shape);
            }
        }

        public double GetTotalArea()
        {
            double totalArea = 0;
            foreach (Shape shape in _shapes)
            {
                totalArea += shape.Area();
            }
            return totalArea;
        }

        public double GetTotalPerimeter()
        {
            double totalPerimeter = 0;
            foreach (Shape shape in _shapes)
            {
                totalPerimeter += shape.Perimeter();
            }
            return totalPerimeter;
        }

        public double GetColouredArea(string colour)
        {
            double colouredArea = 0;
            foreach (Shape shape in _shapes)
            {
                if (shape.Colour == colour)
                {
                    colouredArea += shape.Area();
                }
            }
            return colouredArea;
        }
    }
}
```

Circle
```cs

namespace Shapes
{
    internal class Circle : Shape
    {
        private double _radius;

        public Circle(string colour, double radius) : base(colour)
        {
            _radius = radius;
        }

        public override double Area()
        {
            return Math.PI * _radius * _radius;
        }

        public override double Perimeter()
        {
            return 2 * Math.PI * _radius;
        }

        public override string ToString()
        {
            return $"Circle (ID: {ID}, Colour: {Colour}, Radius: {_radius})";
        }
    }
}


```
Rectangle
```cs
using System;
namespace Shapes
{ 
    internal class Rectangle : Shape
    {
        public double Height { get; }
        public double Width { get; }

        public Rectangle(string colour, double height, double width) : base(colour)
        {
            Height = height;
            Width = width;
        }

        public override double Area()
        {
            return Height * Width;
        }

        public override double Perimeter()
        {
            return 2 * (Height + Width);
        }

        public override string ToString()
        {
            return $"Rectangle (ID: {ID}, Colour: {Colour}, Height: {Height}, Width: {Width})";
        }
    }

}

```
Program
```cs
using Shapes;
{
    ShapeManager manager = new ShapeManager();

    Circle circle1 = new Circle("Red", 5);
    Circle circle2 = new Circle("Green", 7);
    Rectangle rectangle1 = new Rectangle("Blue", 3, 4);
    Rectangle rectangle2 = new Rectangle("Yellow", 2, 6);

    manager.AddShape(circle1);
    manager.AddShape(circle2);
    manager.AddShape(rectangle1);
    manager.AddShape(rectangle2);

    Console.WriteLine(manager.GetTotalArea());
    Console.WriteLine(manager.GetTotalPerimeter());
    Console.WriteLine(manager.GetColouredArea("Red"));

    Console.ReadLine();
}
```
## Semantics 

| Word | definition|
|---|---|
|virtual|allows overriding by a method with the same derived class signature|
|override		| replace the functionality of an inheritied method|
|polymorphism		| having multiple forms of objects, variables, or methods|
|parent/base class reference		| referring to another class and inheriting its properties|
|is and as keywords		| checking/attempting to cast an object to a specific type|
|ToString method		|returns a string representation of the object that called it|
|dependency| a relationship between two or more objects in which an object depends on the other object or objects for its implementation.|



## Reflection

In this section you should reflect upon what you have learnt. This is an important part of the learning process.
- What have you learnt from these exercises?

how to use classes in c#


- How can you apply what you have learnt?

in future programs in c#


- What new features of C# are you now able to use?

classes
