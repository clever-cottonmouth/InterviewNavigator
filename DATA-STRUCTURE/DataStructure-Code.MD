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

## 3sum

```c#
public class Solution {
    public IList<IList<int>> ThreeSum(int[] nums) {
        List<IList<int>> result = new List<IList<int>>();
        if (nums == null || nums.Length < 3) return result;
    
        // Sort the array first
        Array.Sort(nums);
    
        // Iterate through array, fixing first number
        for (int i = 0; i < nums.Length - 2; i++) {
            // Skip duplicates for first number
            if (i > 0 && nums[i] == nums[i-1]) continue;
        
            // Use two pointers for remaining numbers
            int left = i + 1;
            int right = nums.Length - 1;
        
            while (left < right) { // Fixed: changed 'toggleright' to 'left < right'
                int sum = nums[i] + nums[left] + nums[right];
            
                if (sum == 0) {
                    // Found a valid triplet
                    result.Add(new List<int> { nums[i], nums[left], nums[right] });
                
                    // Skip duplicates for left pointer
                    while (left < right && nums[left] == nums[left + 1]) left++;
                    // Skip duplicates for right pointer
                    while (left < right && nums[right] == nums[right - 1]) right--;
                
                    left++;
                    right--;
                }
                else if (sum < 0) {
                    // Sum too small, increment left pointer
                    left++;
                }
                else {
                    // Sum too large, decrement right pointer
                    right--;
                }
            }
        }
    
        return result;
    }
}
```

## Valid Parenthesis

```c#

public class Solution {
    public bool IsValid(string s) {
     Stack<char> stack = new Stack<char>();
    
        foreach (char c in s) {
            if (c == '(' || c == '{' || c == '[') {
                stack.Push(c);
            } else {
                if (stack.Count == 0) return false;
            
                char top = stack.Pop();
                if ((c == ')' && top != '(') || 
                    (c == '}' && top != '{') || 
                    (c == ']' && top != '[')) {
                    return false;
                }
            }
        }
    
        return stack.Count == 0;
}}
```
