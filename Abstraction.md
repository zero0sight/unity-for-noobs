# Abstraction in C#
Data abstraction is the process of hiding certain details and showing only essential information to the user.

Abstraction can be achieved with either abstract calsses or interfaces.

- The `abstract` keyword is used for classes and methods.
- Abstract class is a restricted class that cannot be used to create objects (it must be inherited)
- Abstract class can have both avstract and regular methods.
- `abstract` (need to be inherited) cannot be used with `sealed` (cannot be inherited). They have opposite meanings.
- Abstract method can only be used in abstact class, and it does not have a body. the body is provided by derived class.
- An abstract mehod is implicity a virtual method.
- It is and error to use `static` or `virtual` modifiers in an abstract method declaration.
```C#
abstract class Animal 
{
  public abstract void animalSound();
  public void sleep() 
  {
    Console.WriteLine("Zzz");
  }
}
// you cant create an instance from Animal
// Animal obj = new Animal(); // Will generate an error!

// Derived class (inherit from Animal)
class Pig : Animal
{
  public override void animalSound()
  {
    // The body of animalSound() is provided here
    Console.WriteLine("The pig says: wee wee");
  }
}
```
```C#
// Abstract class
abstract class BaseClass
{
    protected int _x = 100;
    protected int _y = 150;

    // Abstract method
    public abstract void AbstractMethod();

    // Abstract properties
    public abstract int X { get; }
    public abstract int Y { get; }
}

class DerivedClass : BaseClass
{
    public override void AbstractMethod()
    {
        _x++;
        _y++;
    }

    public override int X   // overriding property
    {
        get
        {
            return _x + 10;
        }
    }

    public override int Y   // overriding property
    {
        get
        {
            return _y + 10;
        }
    }

    static void Main()
    {
        var o = new DerivedClass();
        o.AbstractMethod();
        Console.WriteLine($"x = {o.X}, y = {o.Y}");
    }
}
// Output: x = 111, y = 161
```
