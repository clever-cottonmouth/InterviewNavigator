# **DELEGATE**

In C#, a **delegate** is a type that represents references to methods with a specific parameter list and return type. When you instantiate a delegate, you can associate its instance with any method that matches its signature. This allows you to call the method through the delegate instance.

```csharp
using System;
public delegate int performCalc(int x, int y);
public class Program
{
	public static int Add(int x, int y){
	return x+y;
	}
	public static void Main()
	{
		performCalc cal = new performCalc(Add);
		var data = cal(3,5);

		Console.WriteLine(data);
	}
}
```

# EVENT

Events enable a class or object to notify other classes or objects when something of action occurs. The class that sends (or raises) the event is called the publisher and the classes that receive (or handle) the event are called subscribers. There can be multiple subscribers to a single event.

```csharp

using System;// Declare a delegate type
public delegate int performCalc(int x, int y);// Declare a class that has an event
public class Program
{
    // Declare the event using the delegate
    public static event performCalc CalculationPerformed;    // Method that performs addition
    public static int Add(int x, int y)
    {
        return x + y;
    }    // Method to trigger the event
    public static void OnCalculationPerformed(int x, int y)
    {
        // If there are any subscribers to the event, invoke them
        if (CalculationPerformed != null)
        {
            int result = CalculationPerformed(x, y);
            Console.WriteLine($"Event triggered. Result of calculation: {result}");
        }
    }    public static void Main()
    {
        // Subscribe the Add method to the CalculationPerformed event
        CalculationPerformed += new performCalc(Add);    // Call the method that triggers the event
        OnCalculationPerformed(3, 5);
    }
}
```

# **METHOD OVERLOADING AND METHOD OVERRIDING**

CT- Method Overloading

RT - Method Overriding

Method overloading deals with the notion of having two or more methods in the same class with the same name but different arguments.

void foo(int a)
void foo(int a, float b)

```csharp
using System;


public class Program
{
    // Method overload for a single integer parameter
    public void Print(int a)
    {
        Console.WriteLine($"Integer: {a}");
    }

    // Method overload for an integer and a float parameter
    public void Print(int a, float b)
    {
        Console.WriteLine($"Integer: {a}, Float: {b}");
    }

    // Method overload for a single string parameter
    public void Print(string message)
    {
        Console.WriteLine($"Message: {message}");
    }

    public static void Main(string[] args)
    {
        Program ex = new Program();

        ex.Print(5);                // Calls Print(int a)
        ex.Print(5, 3.14f);         // Calls Print(int a, float b)
        ex.Print("Hello World!");   // Calls Print(string message)
    }
}

```

Method overriding means having two methods with the same arguments, but different implementations. One of them would exist in the parent class, while another will be in the derived, or child class.

```csharp
public class BaseClass
{
    public virtual void Display()
    {
        Console.WriteLine("Display from BaseClass");
    }
}public class DerivedClass : BaseClass
{
    public override void Display()
    {
        Console.WriteLine("Display from DerivedClass");
    }
}class Program
{
    static void Main()
    {
        BaseClass obj = new DerivedClass();
        obj.Display();   // Calls Display() from DerivedClass
    }
}
```

# **INTERFACE**

An interface is a contract: An interface is an empty shell. There are only the signatures of the methods, which implies that the methods do not have a body. The interface can't do anything. It's just a pattern.

An abstract class is a class that is only partially implemented by the programmer. It may contain one or more abstract methods. An abstract method is simply a function definition that serves to tell the programmer that the method must be implemented in a child class.

# Struct and Class

A structure is a value type so it is stored on the stack, but a class is a reference type and is stored on the heap.

A structure doesn't support inheritance, and polymorphism, but a class supports both.

By default, all the struct members are public but class members are by default private in nature.

As a structure is a value type, we can't assign null to a struct object, but it is not the case for a class.

# What is the difference between constant and readonly in C#

# Difference between the Equality Operator (==) and Equals() Method in C#

# What is Boxing and Unboxing in C#

# IMPLICITLY AND EXPLICITLY VARIABLE

**implicitly**

var word = "ABC";

var num = 5;

**explicitly**

string word ="ABC";

int num =5;

# DATA HIDING

making the members of a class non-public

```csharp
using System;

class BaseClass{

	public virtual void Method1(){
	Console.WriteLine("BaseClass M1");
	}

	public virtual void Method2(){
	Console.WriteLine("BaseClass M2");
	}
}

class DerivedClass: BaseClass{
	public override void Method1(){
	Console.WriteLine("DerivedClass M1");
	}

	public new void Method2(){
	Console.WriteLine("DerivedClass M2");
	}
}



public class Program
{
	public static void Main()
	{
		BaseClass b = new BaseClass();
		b.Method1();
		b.Method2();

		BaseClass c = new DerivedClass();
		c.Method1();
		c.Method2();

	}
}
```

# ACCESS MODIFIER

Protected:- members can be used in the derived classess, but they can't be used outside.

# Constructor

we can define the constructors in C# are the special types of methods of a class that are executed whenever we create an instance (object) of that class. The Constructors are responsible for two things. One is the object initialization and the other one is memory allocation. The role of the new keyword is to create the object and the role of the constructor is to initialize the variables.

The compiler defined this constructor for us. And we call this an Implicit Constructor. And if we defined the same thing, then it is called an explicit constructor.

If we don’t have a constructor, then we cannot create an instance of the class.

**Static Constructor**

In a static constructor, you cannot use any access specifiers like public, private, and protected.

Static Constructors are responsible for initializing static variables and these constructors are never called explicitly. They are called Implicitly and moreover, these constructors are the first to execute in any class

Static Constructors cannot be parameterized, so overloading of the static constructors is not possible in C#.

**private constructor**

When a class contains a private constructor then we cannot create an object for the class outside of the class. So, private constructors are used to create an object for the class within the same class. Generally, private constructors are used in the Remoting concept.

We need to use the private constructor in C# when the class contains only static members.
