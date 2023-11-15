# Encapsulation in C#
Encapsulation is defined as the wrapping up of data and information under a single unit.

It is the mechanism that binds together the data and the functions that manipulate them.

In a different way, encapsulation is a protective shield that prevents the data from being accessed by the code outside this shield.
- Technically in encapsulation, the variables or data of a class are hidden from any other class and can be accessed only through any member function of its own class in which they are declared.
- As in encapsulation, the data in a class is hidden from other classes, so it is also known as data-hiding.
- Encapsulation can be achieved by: Declaring all the variables in the class as private and using C# Properties in the class to set and get the values of variables.
```C#
// C# program to illustrate encapsulation
using System;
public class DemoEncap {
	// private variables declared
	// these can only be accessed by
	// public methods of class
	private String studentName;
	private int studentAge;
	// using accessors to get and
	// set the value of studentName
	public String Name
	{
		get { return studentName; }
		set { studentName = value; }
	}
	// using accessors to get and
	// set the value of studentAge
	public int Age
	{
		get { return studentAge; }
		set { studentAge = value; }
	}
}
// Driver Class
class GFG {
	// Main Method
	static public void Main()
	{
		// creating object
		DemoEncap obj = new DemoEncap();
		// calls set accessor of the property Name,
		// and pass "Ankita" as value of the
		// standard field 'value'
		obj.Name = "Ankita";
		// calls set accessor of the property Age,
		// and pass "21" as value of the
		// standard field 'value'
		obj.Age = 21;
		// Displaying values of the variables
		Console.WriteLine(" Name : " + obj.Name);
		Console.WriteLine(" Age : " + obj.Age);
	}
}
```
