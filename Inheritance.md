# Inheritance in C#
In C#, it is possible to inherit fields and methods from one class to another.

We group the "inheritance concept" into two categories:
- Derived Class (child) - the class that inherits from another class.
- Base Class (parent) - the class being inherited from.

Inheritance is useful for code reusability: reuse fields and methods of an existing class when you create a new class.

If you don't want other classes to inherit from a class, use the `sealed` keyword

To inherit from a class, use the `:` symbol.
```C#
class Vehicle  // base class (parent) 
{
  public string brand = "Ford";  // Vehicle field
  public void honk()             // Vehicle method 
  {                    
    Console.WriteLine("Tuut, tuut!");
  }
}

class Car : Vehicle  // derived class (child)
{
  public string modelName = "Mustang";  // Car field
}

class Program
{
  static void Main(string[] args)
  {
    // Create a myCar object
    Car myCar = new Car();

    // Call the honk() method (From the Vehicle class) on the myCar object
    myCar.honk();

    // Display the value of the brand field (from the Vehicle class) and the value of the modelName from the Car class
    Console.WriteLine(myCar.brand + " " + myCar.modelName);
  }
}
```
