# Ex8 Detection of Cycle and Finding the Starting Node in a Linked List
## DATE:16-11-25
## AIM:
To write a program that detects a cycle in a linked list and returns the node where the cycle begins.
If there is no cycle, the program should return null without modifying the linked list.
## Algorithm
1.Start slow = head and fast = head.


2.Move slow by 1 step and fast by 2 steps until they meet or fast becomes null.


3.If fast becomes null, return null (no cycle).


4.Move slow to head, keep fast at meeting point.


5.Move both one step at a time until they meet — this node is the cycle start.



## Program:
```
/*
program that detects a cycle in a linked list and returns the node where the cycle begins.
If there is no cycle, the program should return null without modifying the linked list.
Developed by: VIMALA SAHANA W
RegisterNumber: 212223040241 
*/
class DetectCycle {

    // Node structure
    static class Node {
        int data;
        Node next;

        Node(int data) {
            this.data = data;
            this.next = null;
        }
    }

    // Function to detect cycle and return the starting node of the cycle
    static Node detectCycle(Node head) {
        if (head == null || head.next == null) 
            return null;

        Node slow = head;
        Node fast = head;

        // Step 1: Detect if a cycle exists
        while (fast != null && fast.next != null) {
            slow = slow.next;          // slow moves 1 step
            fast = fast.next.next;     // fast moves 2 steps

            if (slow == fast) {        // cycle detected
                break;
            }
        }

        // If no cycle
        if (fast == null || fast.next == null)
            return null;

        // Step 2: Find the node where the cycle begins
        slow = head;
        while (slow != fast) {
            slow = slow.next;
            fast = fast.next;
        }

        return slow;   // this is the start of the cycle
    }

    public static void main(String[] args) {

        // Create linked list: 1 -> 2 -> 3 -> 4 -> 5
        Node head = new Node(1);
        head.next = new Node(2);
        head.next.next = new Node(3);
        head.next.next.next = new Node(4);
        head.next.next.next.next = new Node(5);

        // Creating a cycle: node 5 points to node 3
        head.next.next.next.next.next = head.next.next;

        Node cycleStart = detectCycle(head);

        if (cycleStart != null)
            System.out.println("Cycle starts at node: " + cycleStart.data);
        else
            System.out.println("No cycle detected.");
    }
}

```

## Output:
<img width="374" height="129" alt="image" src="https://github.com/user-attachments/assets/6d97745d-dbe5-4aa5-9f78-553b78468aaa" />




## Result:
The program successfully detects whether a cycle exists in the linked list.
If a cycle is present, it correctly identifies and returns the node where the cycle begins.
