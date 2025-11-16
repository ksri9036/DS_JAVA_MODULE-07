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
