# Ex9 Finding the Longest Length of Nested Set in a Permutation Array

## DATE: 16-11-25


## AIM:
To write a program that finds the length of the longest set s[k] defined as  
s[k] = { nums[k], nums[nums[k]], nums[nums[nums[k]]], … }  
where the iteration stops before a duplicate element occurs. The task is to return the maximum size among all such sets.

## Algorithm
Create a visited array to mark elements already used in any set.

2.For each index k, if it is not visited, start building the set S[k].

3.Keep moving to nums[current], marking each element as visited.

4.Count each step until you reach a visited element (duplicate).

5.Update the maximum count found so far and return it.

## Program:
```java
/*
program that removes all nodes from a linked list whose value matches a given integer (val) and returns the new head of the modified linked list.
Developed by:VIMALA SAHANA W
RegisterNumber:  212223040241
*/
import java.util.Scanner;

class LongestSet {

    public static int longestSetLength(int[] nums) {
        boolean[] visited = new boolean[nums.length];
        int maxLength = 0;

        for (int i = 0; i < nums.length; i++) {
            if (!visited[i]) {
                int count = 0;
                int current = i;

                // Continue until a repeated element appears
                while (!visited[current]) {
                    visited[current] = true;
                    current = nums[current];
                    count++;
                }

                maxLength = Math.max(maxLength, count);
            }
        }

        return maxLength;
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        // Taking user input for array size
        System.out.print("Enter the array size: ");
        int n = sc.nextInt();

        int[] nums = new int[n];

        // Taking user input for array elements
        System.out.println("Enter " + n + " elements:");
        for (int i = 0; i < n; i++) {
            nums[i] = sc.nextInt();
        }

        // Calling function
        int result = longestSetLength(nums);
        System.out.println("Maximum size of S[k] = " + result);

        sc.close();
    }
}

   
```
## OUTPUT
<img width="529" height="271" alt="image" src="https://github.com/user-attachments/assets/76cb8b74-ce8b-4ff3-9e10-d2f7b8b05b6d" />

## RESULT
The program successfully computes the longest length of the nested set s[k] for the given permutation array.
