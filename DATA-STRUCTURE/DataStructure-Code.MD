## Reverse a linked list
```
using System;

class Node
{
    public int Data;
    public Node Next;

    public Node(int data)
    {
        Data = data;
        Next = null;
    }
}

class LinkedList
{
    private Node head;

    // Add a new node to the end of the list
    public void Add(int data)
    {
        Node newNode = new Node(data);
        if (head == null)
        {
            head = newNode;
        }
        else
        {
            Node current = head;
            while (current.Next != null)
            {
                current = current.Next;
            }
            current.Next = newNode;
        }
    }

    // Reverse the linked list
    public void Reverse()
    {
        Node previous = null;
        Node current = head;
        Node next = null;

        while (current != null)
        {
            next = current.Next; // Store the next node
            current.Next = previous; // Reverse the link
            previous = current; // Move previous to current
            current = next; // Move current to next
        }

        head = previous; // Update the head
    }

    // Print the linked list
    public void PrintList()
    {
        Node current = head;
        while (current != null)
        {
            Console.Write(current.Data + " ");
            current = current.Next;
        }
        Console.WriteLine();
    }
}

class Program
{
    static void Main(string[] args)
    {
        LinkedList list = new LinkedList();

        // Add elements to the linked list
        list.Add(1);
        list.Add(2);
        list.Add(3);
        list.Add(4);
        list.Add(5);

        Console.WriteLine("Original List:");
        list.PrintList();

        // Reverse the linked list
        list.Reverse();

        Console.WriteLine("Reversed List:");
        list.PrintList();
    }
}

```