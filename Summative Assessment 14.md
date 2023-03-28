Key Concept - Be able to understand what is meant by an abstract class

An abstract class in C# is a class that cannot be instantiated. It is designed to be inherited by subclasses that either implement or override its methods, which can be either partially implemented or not implemented at all.

Key Concept - Be able to describe the advantages of using an interface (from lecture content)

An interface declares a contract. Implementing an interface enforces your class to be bound to the contract (by providing the appropriate members). Consequently, everything that relies on that contract (a method that relies on the functionality specified by the interface to be provided by your object) can work with your object too.

It improves readability, semantics and maintainability.
Useful in multiple inheritance



Key Concept - Be able to create a concrete implementation of an abstract class

Key Concept - Demonstrate the above skills by completing the challenge exercise

Shape
```cs
namespace OOConsoleMenu
{
    class ShapeManager
    {
        public List<Shape> Shapes { get; private set; }

        public ShapeManager()
        {
            Shapes = new List<Shape>();
        }

        public void AddShape(Shape pShape)
        {
            Shapes.Add(pShape);
        }

        public float TotalArea()
        {
            float total = 0;
            foreach (Shape Shape in Shapes)
            {
                total += Shape.Area();
            }
            return total;
        }

        public float TotalPerimeter()
        {
            float total = 0;
            foreach (Shape Shape in Shapes)
            {
                total += Shape.Perimeter();
            }
            return total;
        }

        public float AreaByColour(Shape.Colour colour)
        {
            float total = 0;
            foreach (Shape shape in Shapes)
            {
                if (shape.ShapeColour == colour)
                {
                    total += shape.Area();
                }
            }
            return total;
        }
    }

    abstract public class Shape
    {
        public enum Colour { Red, Green, Blue }
        public Colour ShapeColour { set; get; }

        public abstract float Area();
        public abstract float Perimeter();
    }

    class Circle : Shape
    {
        public const int MIN_RADIUS = 0;
        public const int MAX_RADIUS = 50;

        private float _Radius;

        public float Radius
        {
            get { return _Radius; }
            set { if (value >= MIN_RADIUS && value <= MAX_RADIUS) { _Radius = value; } }
        }

        public Circle(float radius, Colour colour)
        {
            Radius = radius;
            ShapeColour = colour;
        }

        public override float Area()
        {
            return MathF.PI * _Radius * _Radius;
        }

        public override float Perimeter()
        {
            return 2 * MathF.PI * _Radius;
        }

        public override string ToString()
        {
            return $"{ShapeColour} circle with radius {Radius}.";
        }
    }

    class Square : Shape
    {
        public const int MIN_SIDE = 0;
        public const int MAX_SIDE = 50;

        private float _Width;

        public float Height { get { return _Width; } }
        public float Width
        {
            get { return _Width; }
            set { if (value >= MIN_SIDE && value <= MAX_SIDE) { _Width = value; } }
        }

        public Square(float width, Colour colour)
        {
            Width = width;
            ShapeColour = colour;
        }

        public override float Area()
        {
            return _Width * _Width;
        }

        public override float Perimeter()
        {
            return 4 * _Width;
        }

        public override string ToString()
        {
            return $"{ShapeColour} Square with width {Width}.";
        }
    }

    class Rectangle : Shape
    {
        public const int MIN_SIDE1 = 0;
        public const int MAX_SIDE1 = 50;

        public const int MIN_SIDE2 = 0;
        public const int MAX_SIDE2 = 50;

        private float _Width;
        private float _Height;

        public float Width
        {
            get { return _Width; }
            set { if (value >= MIN_SIDE1 && value <= MAX_SIDE1) { _Width = value; } }
        }

        public float Height
        {
            get { return _Height; }
            set { if (value >= MIN_SIDE2 && value <= MAX_SIDE2) { _Height = value; } }
        }


        public Rectangle(float width, float height, Colour colour)
        {
            Width = width;
            Height = height;
            ShapeColour = colour;
        }

        public override float Area()
        {
            return _Width * _Height;
        }

        public override float Perimeter()
        {
            return ((2 * _Width) + (2 * _Height));
        }

        public override string ToString()
        {
            return $"{ShapeColour} Square with width {Width} and height {Height}.";
        }
    }
}

```

Menu
```cs

using System.Text;

namespace OOConsoleMenu
{
    public static class ConsoleHelpers
    {
        // TODO Can I remove the "int" from this to allow "floats" in a nice way
        public static int GetIntegerInRange(int pMin, int pMax, string pMessage)
        {
            if (pMin > pMax)
            {
                throw new Exception($"Minimum value {pMin} cannot be greater than maximum value {pMax}");
            }

            int result;

            do
            {
                Console.WriteLine(pMessage);
                Console.WriteLine($"Please enter a number between {pMin} and {pMax} inclusive.");

                string userInput = Console.ReadLine();

                try
                {
                    result = int.Parse(userInput);
                }
                catch
                {
                    Console.WriteLine($"{userInput} is not a number");
                    continue;
                }

                if (result >= pMin && result <= pMax)
                {
                    return result;
                }
                Console.WriteLine($"{result} is not between {pMin} and {pMax} inclusive.");
            } while (true);
        }
    }

    abstract class ConsoleMenu : MenuItem
    {
        protected List<MenuItem> _menuItems = new List<MenuItem>();

        public bool IsActive { get; set; }

        public abstract void CreateMenu();

        public override void Select()
        {
            IsActive = true;
            do
            {
                CreateMenu();
                string output = $"{MenuText()}{Environment.NewLine}";
                int selection = ConsoleHelpers.GetIntegerInRange(1, _menuItems.Count, this.ToString()) - 1;
                _menuItems[selection].Select();
            } while (IsActive);
        }

        public override string ToString()
        {
            StringBuilder sb = new StringBuilder();
            sb.AppendLine(MenuText());
            for (int i = 0; i < _menuItems.Count; i++)
            {
                sb.AppendLine($"{i + 1}. {_menuItems[i].MenuText()}");
            }
            return sb.ToString();
        }
    }

    abstract class MenuItem // TODO Make Interface?
    {
        public abstract string MenuText();
        public abstract void Select();
    }

    class ExitMenuItem : MenuItem
    {
        private ConsoleMenu _menu;

        public ExitMenuItem(ConsoleMenu parentItem)
        {
            _menu = parentItem;
        }

        public override string MenuText()
        {
            return "Exit";
        }

        public override void Select()
        {
            _menu.IsActive = false;
        }
    }
}

```

Shape Menu
```cs

using System.Drawing;
using System.Globalization;
using System.Text;

namespace OOConsoleMenu
{
    #region Shape Manager Menus and MenuItems

    class ShapeManagerMenu : ConsoleMenu
    {
        private ShapeManager _manager;

        public ShapeManagerMenu(ShapeManager manager)
        {
            _manager = manager;
        }

        public override void CreateMenu()
        {
            _menuItems.Clear();
            _menuItems.Add(new AddNewShapeMenu(_manager));
            if (_manager.Shapes.Count > 0)
            {
                _menuItems.Add(new ShowShapeDataMenu(_manager));
                _menuItems.Add(new EditExistingShapeMenu(_manager));
                _menuItems.Add(new RemoveExistingShapeMenu(_manager));
            }
            _menuItems.Add(new ExitMenuItem(this));
        }

        public override string MenuText()
        {
            return "Shape Manager Menu";
        }
    }

    
    class ShowShapeDataMenu : ConsoleMenu
    {
        ShapeManager _manager;

        public ShowShapeDataMenu(ShapeManager manager)
        {
            _manager = manager;
        }

        public override void CreateMenu()
        {
            _menuItems.Clear();
            _menuItems.Add(new ShowAreaMenuItem(_manager));
            _menuItems.Add(new ShowPerimeterMenuItem(_manager));
           _menuItems.Add(new SelectColourMenuItem(_manager));
            _menuItems.Add(new ExitMenuItem(this));
        }

        public override string MenuText()
        {
            return "View shape data menu";
        }
    }

    class ShowAreaMenuItem : MenuItem
    {
        private ShapeManager _manager;

        public ShowAreaMenuItem(ShapeManager manager)
        {
            _manager = manager;
        }

        public override string MenuText()
        {
            return "View Total Area";
        }

        
        public override void Select()
        {
            Console.WriteLine((_manager.TotalArea()).ToString());
        }
        
    }

    class ShowPerimeterMenuItem : MenuItem
    {
        private ShapeManager _manager;

        public ShowPerimeterMenuItem(ShapeManager manager)
        {
            _manager = manager;
        }

        public override string MenuText()
        {
            return "View Total Perimeter";
        }

        public override void Select()
        {
            Console.WriteLine((_manager.TotalPerimeter()).ToString());
        }
    }

    class SelectColourMenuItem : MenuItem
    {
        public Shape.Colour Colour { get; private set; }

        private ShapeManager _manager;

        public SelectColourMenuItem(ShapeManager manager)
        {
            _manager = manager;
        }

        public override void Select()
        {
            int selectedIndex = ConsoleHelpers.GetIntegerInRange(1, Enum.GetValues(typeof(Shape.Colour)).Length, ToString()) - 1;
            Colour = (Shape.Colour)selectedIndex;
            Console.WriteLine ((_manager.AreaByColour(Colour)).ToString());
        }

        public override string ToString()
        {
            StringBuilder sb = new StringBuilder($"{MenuText()}{Environment.NewLine}");
            int i = 1;
            foreach (Shape.Colour colour in Enum.GetValues(typeof(Shape.Colour)))
            {
                sb.AppendLine($"{i}. {colour}");
                i++;
            }
            return sb.ToString();
        }

        public override string MenuText()
        {
            return "View Total Area of a Colour";
        }
    }

    class AddNewShapeMenu : ConsoleMenu
    {
        ShapeManager _manager;

        public AddNewShapeMenu(ShapeManager manager)
        {
            _manager = manager;
        }

        public override void CreateMenu()
        {
            _menuItems.Clear();
            _menuItems.Add(new AddCircleMenuItem(_manager));
            _menuItems.Add(new AddSquareMenuItem(_manager));
            _menuItems.Add(new AddRectangleMenuItem(_manager));
            _menuItems.Add(new ExitMenuItem(this));
        }

        public override string MenuText()
        {
            return "Add a new shape menu";
        }
    }

    class EditExistingShapeMenu : ConsoleMenu
    {
        private ShapeManager _manager;

        public EditExistingShapeMenu(ShapeManager manager)
        {
            _manager = manager;
        }

        public override void CreateMenu()
        {
            _menuItems.Clear();
            foreach (Shape shape in _manager.Shapes)
            {
                switch (shape)
                {
                    case Circle:
                        _menuItems.Add(new EditCircleMenu(shape as Circle));
                        break;
                    case Square:
                        _menuItems.Add(new EditSquareMenu(shape as Square));
                        break;
                    case Rectangle:
                        _menuItems.Add(new EditRectangleMenu(shape as Rectangle));
                        break;
                }
            }
            _menuItems.Add(new ExitMenuItem(this));
        }

        public override string MenuText()
        {
            return "Edit an existing shape menu";
        }
    }

    class RemoveExistingShapeMenuItem : MenuItem
    {
        private Shape _shape;
        private ShapeManager _shapeManager;

        public RemoveExistingShapeMenuItem(Shape shape, ShapeManager shapeManager)
        {
            _shape = shape;
            _shapeManager = shapeManager;
        }

        public override string MenuText()
        {
            return _shape.ToString();
        }

        public override void Select()
        {
            for (int i = 0; i < _shapeManager.Shapes.Count; i++)
            {
                if (_shapeManager.Shapes[i] == _shape)
                {
                    _shapeManager.Shapes.RemoveAt(i);
                }
            }
        }
    }

    class RemoveExistingShapeMenu : ConsoleMenu
    {
        private ShapeManager _manager;
        public RemoveExistingShapeMenu(ShapeManager manager)
        {
            _manager = manager;
        }

        public override void CreateMenu()
        {
            _menuItems.Clear();
            foreach (Shape shape in _manager.Shapes)
            {
                _menuItems.Add(new RemoveExistingShapeMenuItem(shape, _manager));
            }
            _menuItems.Add(new ExitMenuItem(this));
        }

        public override string MenuText()
        {
            return "Remove existing shape menu";
        }

        public override void Select()
        {
            base.Select();
        }
    }

    abstract class EditShapeMenu : ConsoleMenu
    {
        protected Shape _shape;

        public EditShapeMenu(Shape shape)
        {
            _shape = shape;
        }

        public override void CreateMenu()
        {
            _menuItems.Clear();
            _menuItems.Add(new ColourShapeMenuItem(_shape));
        }

        public override string MenuText()
        {
            return _shape.ToString();
        }

        public override string ToString()
        {
            return $"Edit {base.ToString()}";
        }
    }


    #endregion

    #region Shape Menus and MenuItems

    abstract class ShapeMenuItem : MenuItem
    {
        private Shape _shape;

        public ShapeMenuItem(Shape shape)
        {
            _shape = shape;
        }
    }

    class ColourShapeMenuItem : MenuItem
    {
        public Shape.Colour Colour { get; private set; }

        private Shape _shape;

        public ColourShapeMenuItem(Shape shape)
        {
            _shape = shape;
        }

        public ColourShapeMenuItem() : this(null)
        {
        }

        public override void Select()
        {
            int selectedIndex = ConsoleHelpers.GetIntegerInRange(1, Enum.GetValues(typeof(Shape.Colour)).Length, ToString()) - 1;
            Colour = (Shape.Colour)selectedIndex;
            if (_shape != null)
            {
                _shape.ShapeColour = Colour;
            }
        }

        public override string ToString()
        {
            StringBuilder sb = new StringBuilder($"{MenuText()}{Environment.NewLine}");
            int i = 1;
            foreach (Shape.Colour colour in Enum.GetValues(typeof(Shape.Colour)))
            {
                sb.AppendLine($"{i}. {colour}");
                i++;
            }
            return sb.ToString();
        }

        public override string MenuText()
        {
            return "Select colour";
        }
    }

    #endregion

    #region Circle Menus and MenuItems

    class EditCircleRadiusMenuItem : MenuItem
    {
        private Circle _circle;

        public EditCircleRadiusMenuItem(Circle circle)
        {
            _circle = circle;
        }

        public override string MenuText()
        {
            return "Edit radius";
        }

        public override void Select()
        {
            _circle.Radius = ConsoleHelpers.GetIntegerInRange(Circle.MIN_RADIUS, Circle.MAX_RADIUS, "Enter new radius");
        }
    }

    class EditCircleMenu : EditShapeMenu
    {
        private Circle _circle;

        public EditCircleMenu(Circle circle) : base(circle)
        {
            _circle = circle;
        }
        public override void CreateMenu()
        {
            base.CreateMenu();
            _menuItems.Add(new EditCircleRadiusMenuItem(_circle));
            _menuItems.Add(new ExitMenuItem(this));
        }
    }

    class AddCircleMenuItem : MenuItem
    {
        private ShapeManager _manager;

        public AddCircleMenuItem(ShapeManager manager)
        {
            _manager = manager;
        }

        public override string MenuText()
        {
            return "Add circle menu";
        }

        public override void Select()
        {
            ColourShapeMenuItem selectColourMenu = new ColourShapeMenuItem();
            selectColourMenu.Select();
            int radius = ConsoleHelpers.GetIntegerInRange(Circle.MIN_RADIUS, Circle.MAX_RADIUS, "What is the radius");
            Shape.Colour colour = selectColourMenu.Colour;
            Circle circle = new Circle(radius, colour);
            _manager.AddShape(circle);
        }
    }

    class EditSquareMenu : EditShapeMenu
    {
        private Square _square;

        public EditSquareMenu(Square square) : base(square)
        {
            _square = square;
        }
        public override void CreateMenu()
        {
            base.CreateMenu();
            _menuItems.Add(new EditSquareWidthMenuItem(_square));
            _menuItems.Add(new ExitMenuItem(this));
        }
    }

    class EditSquareWidthMenuItem : MenuItem
    {
        private Square _square;

        public EditSquareWidthMenuItem(Square square)
        {
            _square = square;
        }

        public override string MenuText()
        {
            return "Edit square width";
        }

        public override void Select()
        {
            _square.Width = ConsoleHelpers.GetIntegerInRange(Square.MIN_SIDE, Square.MAX_SIDE, "Enter new width");
        }
    }

    class AddSquareMenuItem : MenuItem
    {
        private ShapeManager _manager;

        public AddSquareMenuItem(ShapeManager manager)
        {
            _manager = manager;
        }

        public override string MenuText()
        {
            return "Add square menu";
        }

        public override void Select()
        {
            ColourShapeMenuItem selectColourMenu = new ColourShapeMenuItem();
            selectColourMenu.Select();
            int width = ConsoleHelpers.GetIntegerInRange(Square.MIN_SIDE, Square.MAX_SIDE, "What is the width");
            Shape.Colour colour = selectColourMenu.Colour;
            Square square = new Square(width, colour);
            _manager.AddShape(square);
        }
    }

    class EditRectangleMenu : EditShapeMenu
    {
        private Rectangle _rectangle;

        public EditRectangleMenu(Rectangle rectangle) : base(rectangle)
        {
            _rectangle = rectangle;
        }
        public override void CreateMenu()
        {
            base.CreateMenu();
            _menuItems.Add(new EditRectangleWidthMenuItem(_rectangle));
            _menuItems.Add(new EditRectangleHeightMenuItem(_rectangle));
            _menuItems.Add(new ExitMenuItem(this));
        }
    }

    class EditRectangleWidthMenuItem : MenuItem
    {
        private Rectangle _rectangle;

        public EditRectangleWidthMenuItem(Rectangle rectangle)
        {
            _rectangle = rectangle;
        }

        public override string MenuText()
        {
            return "Edit rectangle width";
        }

        public override void Select()
        {
            _rectangle.Width = ConsoleHelpers.GetIntegerInRange(Rectangle.MIN_SIDE1, Rectangle.MAX_SIDE1, "Enter new width");
        }
    }

    class EditRectangleHeightMenuItem : MenuItem
    {
        private Rectangle _rectangle;

        public EditRectangleHeightMenuItem(Rectangle rectangle)
        {
            _rectangle = rectangle;
        }

        public override string MenuText()
        {
            return "Edit rectangle height";
        }

        public override void Select()
        {
            _rectangle.Width = ConsoleHelpers.GetIntegerInRange(Rectangle.MIN_SIDE2, Rectangle.MAX_SIDE2, "Enter new height");
        }
    }

    class AddRectangleMenuItem : MenuItem
    {
        private ShapeManager _manager;

        public AddRectangleMenuItem(ShapeManager manager)
        {
            _manager = manager;
        }

        public override string MenuText()
        {
            return "Add rectangle menu";
        }

        public override void Select()
        {
            ColourShapeMenuItem selectColourMenu = new ColourShapeMenuItem();
            selectColourMenu.Select();
            int width = ConsoleHelpers.GetIntegerInRange(Rectangle.MIN_SIDE1, Rectangle.MAX_SIDE1, "What is the width");
            int height = ConsoleHelpers.GetIntegerInRange(Rectangle.MIN_SIDE2, Rectangle.MAX_SIDE2, "What is the height");
            Shape.Colour colour = selectColourMenu.Colour;
            Rectangle rectangle = new Rectangle(width, height, colour);
            _manager.AddShape(rectangle);
        }
    }
    #endregion
}

```

Program
```cs
using OOConsoleMenu;
using System.Runtime.InteropServices;

Console.WriteLine("Hello, OO Console Menu!");

ShapeManager manager = new ShapeManager();

new ShapeManagerMenu(manager).Select();
```


## Semantics 

| Word | definition|
|---|---| 
|abstract class| can only operate when inherited, cannot be instantiated	|	
|abstract method| a method inherited and overwritten from an abstract class and can only be called from the child class|	
|concrete class|	allows creating an instance or an object using the new keyword	|
|sealed class		|cannot be inherited by any class but can be instantiated|
|sealed method	|	cant be overwritten|
|interface		|a code structure that defines a contract between an object and its user, used to define members and methods|
|observer pattern| allows objects to notify each other of changes in their state|


	



## Reflection

In this section you should reflect upon what you have learnt. This is an important part of the learning process.
- What have you learnt from these exercises?

how to use classes in c#


- How can you apply what you have learnt?

in future programs in c#


- What new features of C# are you now able to use?

classes
