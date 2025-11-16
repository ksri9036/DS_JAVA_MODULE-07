# Ex6 Right Rotation LinkedList
## DATE: 16-11-25
## AIM:
To write a Java  program to:
Create a singly linked list.
Rotate the linked list to the right by k positions.
Display the rotated linked list.
## Algorithm
1.Count the number of nodes in the linked list.

2.Make the list circular by connecting the last node to the first.

3.Reduce k using k = k % length.

4.Move (length − k) steps from the start to find the new tail.

5.Break the circle after the new tail → the next node becomes the new head.
   

## Program:
```
/*
Program to  Right Rotation LinkedList
Developed by: VIMALA SAHANA W 
RegisterNumber: 212223040241 
*/
class RotateLinkedList {

    // Node structure
    static class Node {
        int data;
        Node next;

        Node(int data) {
            this.data = data;
            this.next = null;
        }
    }

    // Function to rotate the linked list to the right by k positions
    static Node rotateRight(Node head, int k) {
        if (head == null || head.next == null || k == 0)
            return head;

        // Step 1: count the number of nodes
        Node temp = head;
        int length = 1;
        while (temp.next != null) {
            temp = temp.next;
            length++;
        }

        // Step 2: connect last node to head to make it circular
        temp.next = head;

        // Step 3: adjust k if greater than length
        k = k % length;
        int stepsToNewHead = length - k;

        // Step 4: find the new tail (node just before new head)
        Node newTail = head;
        for (int i = 1; i < stepsToNewHead; i++) {
            newTail = newTail.next;
        }

        // Step 5: new head is next of new tail
        Node newHead = newTail.next;

        // Step 6: break the circle
        newTail.next = null;

        return newHead;
    }

    // Function to display the linked list
    static void display(Node head) {
        Node current = head;
        while (current != null) {
            System.out.print(current.data + " ");
            current = current.next;
        }
        System.out.println();
    }

    // Main program
    public static void main(String[] args) {
        // Create linked list: 10 -> 20 -> 30 -> 40 -> 50
        Node head = new Node(10);
        head.next = new Node(20);
        head.next.next = new Node(30);
        head.next.next.next = new Node(40);
        head.next.next.next.next = new Node(50);

        System.out.println("Original Linked List:");
        display(head);

        int k = 2;  // rotate by 2 positions

        head = rotateRight(head, k);

        System.out.println("Rotated Linked List (Right by " + k + "):");
        display(head);
    }
}

```

## Output:

<img width="434" height="193" alt="image" src="https://github.com/user-attachments/assets/5d42774d-9585-45b1-a571-87a63be0d8f2" />


## Result:
Thus, the java program to perfom right rotation on linked list is implemented successfully.
