# Abstraction in C#
Data abstraction is the process of hiding certain details and showing only essential information to the user.

Abstraction can be achieved with either abstract calsses or interfaces.

- The `abstract` keyword is used for classes and methods.
- Abstract class is a restricted class that cannot be used to create objects (it must be inherited)
- Abstract method can only be used in abstact class, and it does not have a body. the body is provided by derived class.
- Abstract class can have both avstract and regular methods.
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
