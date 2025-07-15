# CLI-Common Language Infrastructure

cmd: developer command prompt->ildasm

platform-neutral environment for executing applications written in multiple high-level programming languages

c# code -> IL code -> Jit Compiler-> Hardware

## CLR-Common Language Runtime

Runtime enginer to execute application

## CLS-Common Language Specification

## BCL- Base Class Library

Console, String, StringBuilder, convert, Thread, Task

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

# Ref and Out

when you want multiple outputs from a function, then you need to use the ref and out parameters in C#.

if you are declaring some out variables, then it is mandatory or compulsory to initialize or update the out variables inside the method body else we will get a compiler error. But with the ref, updating the ref variable inside a method is optional.

initializing the ref parameter is mandatory before passing such variables to the method while initializing the out-parameter variables is optional in C#.

**Note:** The point that you need to remember is that the ref keyword is used to pass data pass in bi-directional and the out keyword is used to pass the data only in unidirectional i.e. returning the data.

```csharp
using System;
namespace RefvsOutDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            //First Declare the Variables
            int Addition = 0;
            int Multiplication = 0;
            int Subtraction = 0;
            int Division = 0;
            //While calling the Method, decorate the out keyword for out arguments
            //Addition, Multiplication, Subtraction, and Division variables values will be updated by Math Function
            Math(200, 100, out Addition, out Multiplication, out Subtraction, out Division);
            Console.WriteLine($"Addition: {Addition}");
            Console.WriteLine($"Multiplication: {Multiplication}");
            Console.WriteLine($"Subtraction: {Subtraction}");
            Console.WriteLine($"Division: {Division}");
        
            Console.ReadKey();
        }
        //Declaring Method with out Parameters
        public static void Math(int number1, int number2, out int Addition,
            out int Multiplication, out int Subtraction, out int Division)
        {
            Addition = number1 + number2; //This will Update the Addition variable Declared in Main Method
            Multiplication = number1 * number2; //This will Update the Multiplication variable Declared in Main Method
            Subtraction = number1 - number2; //This will Update the Subtraction variable Declared in Main Method
            Division = number1 / number2; //This will Update the Division variable Declared in Main Method
        }
    }
}
```

# Type Conversion

'Type Conversion' is a process of convert a value from one type (source type) to another type (destination type).

Eg: int -> long

1. Implicit Casting

(from lower-numerical-type to higher-numerical-type)

2. Explicit Casting

(from higher-numerical-type to lower-numerical-type)

# Delegate

# EVENT

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

## **What is a Collection in C#?**

So in simple words, we can say a Collection in C# is a dynamic array**.** That means the collections in C# have the capability of storing multiple values but with the following features.

1. Size can be increased dynamically.
2. We can insert an element into the middle of a collection.
3. It also provides the facility to remove or delete elements from the middle of a collection.

The collections in C# are classes that represent a group of objects. With the help of C# Collections, we can perform different types of operations on objects such as Store, Update, Delete, Retrieve, Search, and Sort objects, etc. In short, all the data structure work can be performed by collections in C#. That means Collections standardize the way in which the objects are handled by our program.

##### **Types of Collections in C#**

There are 3 ways to work with collections. The three namespaces are given below:

1. System.Collections classes
2. System.Collections.Generic classes
3. System.Collections.Concurrent classes

## What is the difference between const and readonly in C#?

`const`: Can't be changed anywhere.

`readonly`: This value can only be changed in the constructor. Can't be changed in normal functions.

# FOR AND FOREACH

The foreach statement is used to iterate through the collection to get the information that you want, but can not be used to add or remove items from the source collection to avoid unpredictable side effects. If you need to add or remove items from the source collection, use a for loop.

If you are iterating through a collection of items, and do not care about the index values then foreach is more convenient, easier to write and safer: you can't get the number of items wrong.

If you need to process every second item in a collection for example, or process them ion the reverse order, then a for loop is the only practical way.
