# Polymorphism
Polymorphism means "many forms", and it occurs when we have many classes that are related to each other by inheritance.

Like we specified in the previous chapter; Inheritance lets us inherit fields and methods from another class. Polymorphism uses those methods to perform different tasks. This allows us to perform a single action in different ways.

```C#
class Animal  // Base class (parent) 
{
  public void animalSound() 
  {
    Console.WriteLine("The animal makes a sound");
  }
}

class Pig : Animal  // Derived class (child) 
{
  public void animalSound() 
  {
    Console.WriteLine("The pig says: wee wee");
  }
}

class Program 
{
  static void Main(string[] args) 
  {
    Animal myAnimal = new Animal();  // Create a Animal object
    Animal myPig = new Pig();  // Create a Pig object

    myAnimal.animalSound();
    myPig.animalSound(); // Parent method will be called.
  }
}
// Output:
// The animal makes a sound
// The animal makes a sound
```
The output from the example above was probably not what you expected. That is because the base class method overrides the derived class method, when they share the same name.

However, C# provides an option to override the base class method, by adding the virtual keyword to the method inside the base class, and by using the override keyword for each derived class methods:

```C#
class Animal  // Base class (parent) 
{
  public virtual void animalSound() 
  {
    Console.WriteLine("The animal makes a sound");
  }
}

class Pig : Animal  // Derived class (child) 
{
  public override void animalSound() 
  {
    Console.WriteLine("The pig says: wee wee");
  }
}


class Program 
{
  static void Main(string[] args) 
  {
    Animal myAnimal = new Animal();  // Create a Animal object
    Animal myPig = new Pig();  // Create a Pig object

    myAnimal.animalSound();
    myPig.animalSound();
  }
}
// Output:
// The animal makes a sound
// The pig says: wee wee
```
There are two types of polymorphism:
- Compile-Time Polymorphism / Static Polymorphism
- Run-Time Polymorphism / Dynamic Polymorphism

## Compile-Time Polymorphism
In compile time polymorphism, the compiler identifies which method is being called at the compile time.

In C#, we achieve compile time polymorphism through 2 ways:

- Method overloading
  - different numbers of parameter
  - types of parameter
```C#
void totalSum() {...}
void totalSum(int a) {...}
void totalSum(int a, int b) {...}
```
```C#
void totalSum(int a, int b) {...}
void totalSum(double a, double b) {...}
```
- Operator overloading




