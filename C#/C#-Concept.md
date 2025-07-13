# Value Type vs Reference Types

System.value

struct, int char

Syste,.Object

classes,delegate, string, array

# What is a managed and unmanaged code

Managed code lets you run the code on a managed CLR runtime environment in the .NET framework.
Unmanaged code is when the code doesn’t run on CLR, it is an unmanaged code that works outside the .NET framework.

# Garbage Collection

Garbage Collection is a process of deleting objects from memory, to free-up memory; so the same memory can be re-used

**When GC gets triggered?**

There are NO specific timings for GC to get triggered.

GC automatically gets trigged in the following conditions:

- When the "heap" is full or free space is too low.
- When we call GC.Collect() explicitly.

#### Generations in GC

Heap contains three segments (called generations):

* Generation 2 [Long-Lived Generation]
* Generation 1 [Survival Generation]
* Generation 0 [Short-Lived Generation]

# IDisposable

The "IDisposable" interface of "System" namespace, has a method called "Dispose", which is used to close un-managed resources that are created during the life-time of the object.

#### Using Declaration

You can prefix "using" keyword before the local variable declaration, in order to call "Dispose" method when that variable goes out of scope.

**Creating object**

<pre class="prettyprint linenums prettyprinted" role="presentation"><ol class="linenums"><li class="L0"><p><span class="kwd">public</span><span class="pln"></span><span class="kwd">void</span><span class="pln"></span><span class="typ">Method</span><span class="pun">(</span><span class="pln"></span><span class="pun">)</span></p></li><li class="L1" data-node-id="20240811143924-8sk6xs9"><p><span class="pun">{</span></p></li><li class="L2"><p><span class="pln"></span><span class="kwd">using</span><span class="pln"></span><span class="typ">ClassName</span><span class="pln"> referenceVariable </span><span class="pun">=</span><span class="pln"></span><span class="kwd">new</span><span class="pln"></span><span class="typ">ClassName</span><span class="pun">(</span><span class="pln"></span><span class="pun">);</span></p></li><li class="L3" data-node-id="20240811143924-9hjeuzn"><p><span class="pln"> </span></p></li><li class="L4"><p><span class="pln"></span><span class="com">//do work here</span></p></li><li class="L5" data-node-id="20240811143924-yfl589q"><p><span class="pln"> </span></p></li><li class="L6"><p><span class="pun">}</span><span class="pln"></span><span class="com">//Dispose will be called automatically here</span></p></li></ol></pre>

# Destructor

Destructor is a special method of the class, which is used to close un-managed resources (such as database connections and file connections), that are opened during the class execution.

# Base Keyword

The `base` keyword is used to refer to the base class when chaining constructors or when you want to access a member (method, property, anything) in the base class that has been overridden or hidden in the current class. For example,

```
using System;

public class Program
{
    class A {
        protected virtual void Foo() {
            Console.WriteLine("I'm A");
        }
    }

    class B : A {
        protected override void Foo() {
            Console.WriteLine("I'm B");
        }

        public void Bar() {
            Foo();       // Calls Foo() from class B
            base.Foo();  // Calls Foo() from class A
        }
    }

    public static void Main(string[] args)
    {
       new B().Bar();
    }
}

```

would output

```csharp
I'm B
I'm A
```

# Ref Keyword

```
class Student
{
    //public field
    public int grade = 2;

    //public method
    public void PrintGrade()
    {
        System.Console.WriteLine("Grade: " + grade);
    }

    //public method with ref return
    public ref int DoWork()
    {
        //return reference of 'grade' field
        return ref grade;
    }
}

class Program
{
    static void Main()
    {
        //creating object of Student
        Student s = new Student();

        //call PrintGrade
        s.PrintGrade();

        //call DoWork
        ref int g = ref s.DoWork();

        //update the value of 'ref return'
        g = 5;

        //call PrintGrade after updating the value of 'ref return'
        s.PrintGrade(); //Output: 5

        System.Console.ReadKey();
    }
}

```

# Out Keyword

The `out` keyword is especially useful when a method needs to return more than one value since more than one `out` parameter can be used

# Type Conversion

'Type Conversion' is a process of convert a value from one type (source type) to another type (destination type).

Eg: int -> long

1. Implicit Casting

(from lower-numerical-type to higher-numerical-type)

2. Explicit Casting

(from higher-numerical-type to lower-numerical-type)

# Delegate

using System;

// Delegate declaration
public delegate int PerformCalculation(int x, int y);

class Program
{
    // Method that matches the delegate signature
    public static int Add(int a, int b)
    {
        return a + b;
    }

    static void Main(string[] args)
    {
        // Instantiating the delegate
        PerformCalculation calc = new PerformCalculation(Add);

    // Calling the method through the delegate
        int result = calc(5, 3);
        Console.WriteLine(result); // Output: 8
    }
}

# For And Foreach

for-for is faster, need modification,

foreach-no need modification, enumeration, inside loop Add method not recommended.

# Generic Method

```csharp
public static T Add<T>(T number1, T number2)
{
    dynamic a = number1;
    dynamic b = number2;
    return a + b;
}
```

# Thread

Threads in C# allow you to perform multiple operations simultaneously, making your applications more responsive and efficient.

You can control thread behavior using various methods and properties:

* **Start** : Begins thread execution.
* **Join** : Waits for the thread to finish.
* **Abort** : Stops the thread (not recommended in .NET Core).
* **Sleep** : Pauses the thread for a specified time.

# 2D Array

**int[,] A = {{2, 5, 9},{6, 9, 15}};**

# Task

**Task** represents an asynchronous operation. It’s part of the `System.Threading.Tasks` namespace and is used to perform operations asynchronously on thread pool threads rather than the main thread.

# InstanceOf

We cannot create an instance of an interface.

We cannot create an instance of an Abstract Class.

No, you cannot create an instance of a static class in C#.

# Inherit

No, you cannot inherit a static class in C#

you  **cannot inherit a private class** .

Yes, you can inherit an abstract class in C#.

Yes, in C#, you can inherit one interface from another.

## Stack and Heap Memory
Stack Memory:Stores value types (e.g., int, struct) and method data (e.g., local variables, return addresses).
Fast, fixed-size, scope-based (auto-cleared when method ends).
Thread-specific, inherently thread-safe.

Heap Memory:Stores reference types (e.g., class, string, arrays).
Dynamic, managed by Garbage Collector (GC) for allocation/deallocation.
Slower, shared across threads, requires synchronization.

