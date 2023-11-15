# Object Oriented Programming in C#
Everything is object. Even you!

Remember these Concepts of OOP
- Abstraction
- Encapsulation
- Inheritance
- Polymorphism

## Abstraction
Abstraction is hide the details and hide how it is done, Show we can do that thing you asked for.

Abstraction in c# is the process to hide the internal details and show only the functionality.

Abstraction is To represent the essential feature without representing the background details.

```C#
// MobilePhone can call and use messages thats all you need to know!
public abstract class MobilePhone
{
  public abstract void Call();
  public abstract void Message();
}
```

## Encapsulation
Encapsulation binds code and the data it manipulates and keeps them safe from outside interference and misuse.

Encapsulation is achieved through use of access modifires, such as `private`, `protected` and `internal`.
```C#
// You can't modify speed outside of Car class.
public class Car
{
    public int Speed { get; private set; }
}
```
```C#
// You can't modify _speed from outside unless you go through Speed validation that Car class provides.
public class Car
{
    private int _speed;
    public int Speed
    {
        get
        {
            return _speed;
        }
        set
        {
            if (_speed > 0) _speed = value;
            else _speed = 0;
        }
    }
}
```

## Inheritance
When a class includes a property of another class, it is known as inheritance.

Inheritance is a process of object reusablity.
```C#
public class Parent
{
    public Parent()
    {
        Console.WriteLine("Parent Constructor.");
    }
    public void print()
    {
        Console.WriteLine("I can print.");
    }
}

public class Child: Parent
{
    public Child()
    {
        Console.WriteLine("Child Constructor.");
    }
}

class Program
{
    static void Main(string[] args)
    {
        Child firstChild = new Child();
        firstChild.print();
    }
}
// Output:
// Parent Constructor.
// Child Constructor.
// I can print.
```

## Polymorphism
Polymorphism means one name, many forms.

One function behaves in different forms. In other words "Many forms of a single object is called Polymorphism".
```C#
// Static or compile-time polymorphism (overloading)
public class TestData
{
    public int Add(int a, int b, int c)
    {
        return a + b + c;
    }
    public int Add(int a, int b)
    {
        return a + b;
    }
}
```
```C#
// Dynamic or run-time polymorphism (overriding)
public class Drawing
{
    public virtual double Area()
   {
         return 0;
   }
}

public class Circle : Drawing
{
    public double Radius { get; set; }
    public Circle()
    {
        Radius = 5;
    }
    public override double Area()
    {
        return (3.14) * Math.Pow(Radius, 2);
    }
}
```
