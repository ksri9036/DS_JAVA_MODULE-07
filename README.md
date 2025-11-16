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

# Ex7 Removal of Nodes with a Specific Value from a Linked List
## DATE:16-11-25
## AIM:
To write a java  program that removes all nodes from a linked list whose value matches a given integer (val) and returns the new head of the modified linked list.

## Algorithm
1.Move head forward until it reaches a node whose value is not equal to val.

2.If the list becomes empty, return null.

3.Start from the new head and traverse the list using a pointer (current).

4.If current.next contains val, skip that node

5.Otherwise, move to the next node. Continue until the end, then return the modified head.
## Program:
```
/*
program that removes all nodes from a linked list whose value matches a given integer (val) and returns the new head of the modified linked list.
Developed by: VIMALA SAHANA W
RegisterNumber: 212223040241
*/
class RemoveNodes {

    // Node structure
    static class Node {
        int data;
        Node next;

        Node(int data) {
            this.data = data;
            this.next = null;
        }
    }

    // Function to remove nodes equal to val
    static Node removeElements(Node head, int val) {
        // Step 1: Remove matching nodes at the beginning
        while (head != null && head.data == val) {
            head = head.next;
        }

        // If list becomes empty
        if (head == null) return null;

        // Step 2: Remove matching nodes in the rest of the list
        Node current = head;
        while (current.next != null) {
            if (current.next.data == val) {
                current.next = current.next.next; // Skip node
            } else {
                current = current.next; // Move ahead
            }
        }

        return head; // Return new head
    }

    // Function to display linked list
    static void display(Node head) {
        Node temp = head;
        while (temp != null) {
            System.out.print(temp.data + " ");
            temp = temp.next;
        }
        System.out.println();
    }

    public static void main(String[] args) {

        // Creating linked list: 1 -> 2 -> 6 -> 3 -> 6 -> 4
        Node head = new Node(1);
        head.next = new Node(2);
        head.next.next = new Node(6);
        head.next.next.next = new Node(3);
        head.next.next.next.next = new Node(6);
        head.next.next.next.next.next = new Node(4);

        System.out.println("Original Linked List:");
        display(head);

        int val = 6;

        head = removeElements(head, val);

        System.out.println("Linked List after removing value " + val + ":");
        display(head);
    }
}

```

## Output:

<img width="424" height="185" alt="image" src="https://github.com/user-attachments/assets/20607bd4-8a25-46d2-9376-4773ed11c046" />



## Result:
The java program successfully removes all nodes with the specified value (val) from the linked list and returns the new head.
