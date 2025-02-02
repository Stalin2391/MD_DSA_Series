# Agenda 
### Linked List Basics
### Search for element x
### Insert / Delete of any Node 
### Linked List Cycle
### Reverse the Linked List
### Deep copy
-----------


# Linked List Basics 

### Linked List basic structure:

<img width="1423" alt="linked list basic structure" src="https://github.com/user-attachments/assets/f7e21e8a-8fb4-4e87-960b-aa763a43bd96" />


Basic linked list structure would be like this:

```java

class Node{
      int val;
      Node next;

      public Node(int val){
            this.val = val;
            next = null;
      }
}

```

#  Insert a Node at Front/Beginning of a Linked List

Given a linked list, the task is to insert a new node at the beginning/start/front of the linked list.

```
Example 1:

Input: LinkedList = 4->8->16->24, NewNode = 12
Output: 12 4 8 16 24

Example 2:

Input: LinkedList = 2->10, NewNode = 1
Output: 1 2 10

```

### Code:

```java

addFirstNode(Node head, int x){
      Node firstNode = new Node(x);
      firstNode.next = head;
      head = firstNode;
}

```

## DRY RUN: 

<img width="1445" alt="Beginning of a Linked List" src="https://github.com/user-attachments/assets/96e60003-bb2d-4a05-bff6-8368a49a38c3" />


##  Insert a Node at Last of a Linked List :

Given a linked list, the task is to insert a new node at the Last of the linked list.

```
Example 1:

Input: LinkedList = 4->8->16->24, NewNode = 30
Output: 4 8 16 24 30

Example 2:

Input: LinkedList = 2->10, NewNode = 15
Output: 2 10 15

```

## Code :

```java

addLastNode(Node head int x){
      if(head == null) return null;
      if(head.next == null) return null;
      Node temp = head;
      while(temp.next != null){
            temp = temp.next;
      }
      Node lastNode = new Node(x);
      temp.next = lastNode;
      return head;
}

```

#  Delete in Linked List

You are given the head of a linked list A and an integer B. Delete the B-th node from the linked list.

Note : Follow 0-based indexing for the node numbering.

```

Example Input

Input 1:
A = 1 -> 2 -> 3
B = 1


Input 2:
A = 4 -> 3 -> 2 -> 1
B = 0

Example Output

Output 1:
1 -> 3

Output 2:
3 -> 2 -> 1

```

### Edge case when B is 0 ----> DRY RUN:

### Code:

```java

deleteFirstNode(Node head){
      if(head == null) return;
      head = head.next;
}

```

<img width="1433" alt="Delete in position" src="https://github.com/user-attachments/assets/b770b0f1-9fbf-466a-a734-4e7f8c46a17c" />

If O - th Node Deleted the output would be :

output : 2 -> 3 -> 4 -> 5


### DRY RUN: Delete the B-th Node from the linked list:

<img width="1423" alt="Delete Edge case" src="https://github.com/user-attachments/assets/a39f9980-cbee-489c-94a2-4bacd19fb68e" />

If B - th Node (B = 3) Deleted the output would be :

output : 1 -> 2 -> 3 -> 5


## Delete Node in a Linked List :

There is a singly-linked list head and we want to delete a node node in it.

You are given the node to be deleted node. You will not be given access to the first node of head.

All the values of the linked list are unique, and it is guaranteed that the given node node is not the last node in the linked list.

Delete the given node. Note that by deleting the node, we do not mean removing it from memory. We mean:

The value of the given node should not exist in the linked list.
The number of nodes in the linked list should decrease by one.
All the values before node should be in the same order.
All the values after node should be in the same order.
Custom testing:

For the input, you should provide the entire linked list head and the node to be given node. node should not be the last node of the list and should be an actual node in the list.
We will build the linked list and pass the node to your function.
The output will be the entire list after calling your function.

```
Example 1:
Input: head = [4,5,1,9], node = 5
Output: [4,1,9]

Explanation: You are given the second node with value 5, the linked list should become 4 -> 1 -> 9 after calling your function.

Example 2:

Input: head = [4,5,1,9], node = 1
Output: [4,5,9]

Explanation: You are given the third node with value 1, the linked list should become 4 -> 5 -> 9 after calling your function.

```

### code:

```java

public void deleteNode(ListNode node) {
      node.val = node.next.val;
      node.next = node.next.next;
}

```

### Delete the Middle Node of a Linked List [ Medium ] :

You are given the head of a linked list. Delete the middle node, and return the head of the modified linked list.

The middle node of a linked list of size n is the ⌊n / 2⌋th node from the start using 0-based indexing, where ⌊x⌋ denotes the largest integer less than or equal to x.

For n = 1, 2, 3, 4, and 5, the middle nodes are 0, 1, 1, 2, and 2, respectively.

```
Example 1:

Input: head = [1,3,4,7,1,2,6]
Output: [1,3,4,1,2,6]

Explanation:
The above figure represents the given linked list. The indices of the nodes are written below.
Since n = 7, node 3 with value 7 is the middle node, which is marked in red.
We return the new list after removing this node.

Example 2:

Input: head = [1,2,3,4]
Output: [1,2,4]
Explanation:
The above figure represents the given linked list.
For n = 4, node 2 with value 3 is the middle node, which is marked in red.

Example 3 :

Input: head = [2,1]
Output: [2]
Explanation:
The above figure represents the given linked list.
For n = 2, node 1 with value 1 is the middle node, which is marked in red.
Node 0 with value 2 is the only node remaining after removing node 1.

```

### Code : (Slow and Fast Pointer) - Approach 1:

```java

public ListNode deleteMiddle(ListNode head) {
        
        if (head == null || head.next == null) {
            return null;
        }
      
        ListNode fast = head;
        ListNode slow = head;
        ListNode prev = null;
      
        while(fast != null && fast.next != null){
            fast = fast.next.next;
            prev = slow;
            slow = slow.next;
        }
      
        if(prev != null) prev.next = slow.next;
      
        return head;

}

```

#### Approach 2 : 

```java


public ListNode deleteMiddle(ListNode head) {
        if (head == null || head.next == null) {  // If the list is empty or has only one node.
            return null;
        }

        // Count the number of nodes
        int count = 0;
        ListNode temp = head;
        while (temp != null) {
            count++;
            temp = temp.next;
        }

        // Find the middle node index
        int middleIndex = count / 2;
        temp = head;
        ListNode prev = null;
        
        // Traverse again to the middle node and remove it
        for (int i = 0; i < middleIndex; i++) {
            prev = temp;
            temp = temp.next;
        }

        // Remove the middle node by linking the previous node to the next of the middle node
        if (prev != null) {
            prev.next = temp.next;
        }

        return head;
    }


```

# Remove Duplicates from Sorted List : [ Easy ]

Given the head of a sorted linked list, delete all duplicates such that each element appears only once. Return the linked list sorted as well.

```
Example 1:

Input: head = [1,1,2]
Output: [1,2]

Example 2:

Input: head = [1,1,2,3,3]
Output: [1,2,3

```

### Code :

```java

public ListNode deleteDuplicates(ListNode head) {
    if(head == null) return head;

    ListNode current = head;

    while(current != null && current.next != null) {
        if(current.val = current.next.value) {
            current.next = current.next.next;
        }else {
            current = current.next;
        }
    }
    return head;
}

```

# Linked List Cycle

Given head, the head of a linked list, determine if the linked list has a cycle in it.

There is a cycle in a linked list if there is some node in the list that can be reached again by continuously following the next pointer. Internally, pos is used to denote the index of the node that tail's next pointer is connected to. Note that pos is not passed as a parameter.

Return true if there is a cycle in the linked list. Otherwise, return false.

```
Example 1 :
Input: head = [3,2,0,-4], pos = 1
Output: true
Explanation: There is a cycle in the linked list, where the tail connects to the 1st node (0-indexed).

Example 2 :

Input: head = [1,2], pos = 0
Output: true
Explanation: There is a cycle in the linked list, where the tail connects to the 0th node.

Example 3 :

Input: head = [1], pos = -1
Output: false
Explanation: There is no cycle in the linked list.

```
## Brute Force Idea :

Brute Force Idea for Cycle Detection in a Linked List:

- Start with the head of the linked list.
- Traverse through each node and store the addresses of visited nodes in a set or array.
- For each node, check if its address has already been encountered.
  - If it has, a cycle exists (because we’ve revisited a node).
  - If it hasn’t, continue traversing to the next node.
- If the traversal ends and no node was revisited, there is no cycle.

```java

public boolean hasCycle(ListNode head) {

    if(head == null || head.next == null) return false;

    HashSet<Integer> set = new HashSet<>();

    ListNode current = head;

    while(current != null){

        if(set.contains(current)) return true;
        set.add(current);
        current = current.next;

    }

    return false;

}


```

## Optimized Idea :

**Floyd’s Tortoise and Hare Algorithm**

Steps to follow Floyd's Tortoise algorithm:
- Initialize two pointers, slow and fast, both starting at the head of the linked list.
- Move slow by one step and fast by two steps in each iteration.
- If there is no cycle, fast will eventually reach the end of the list (`fast == NULL || fast.next == NULL`).
- If there is a cycle, slow and fast will meet at some point (since fast will eventually catch up to slow due to the cycle).
- If the pointers meet, a cycle is detected. If fast reaches the end of the list, no cycle exists.


```java

public boolean hasCycle(ListNode head) {
    if(head == null || head.next == null) return false;

    ListNode slow = head;
    ListNode fast = head;

    while(fast != null && fast.next != null){
        slow = slow.next;
        fast = fast.next.next;

        if(slow == fast) return true;
    }

    return true;
}

```

# Reverse Linked List

Given the head of a singly linked list, reverse the list, and return the reversed list.

```
Example 1:

Input: head = [1,2,3,4,5]
Output: [5,4,3,2,1]

Example 2:

Input: head = [1,2]
Output: [2,1]

Example 3:

Input: head = []
Output: []

```

**Follow up:** A linked list can be reversed either iteratively or recursively. Could you implement both?


```java

public ListNode reverseList(ListNode head) {
    if(head == null) return null;
    if(head.next == null) return head;

    ListNode prev = null;
    ListNode current = head;

    while(current != null){
        ListNode nextNode = current.next;
        current.next = prev;
        prev = current;
        current = nextNode;
    }

    return prev;
}

```

# Search for element x

Given a target x iterate and check if **Target** exists or not?. 




## Approach 1:


```java

public static boolean isTargetExist(int[] arr, int target) {
    int N = arr.length;

    for(int i = 0; i < N; i++){
        if(arr[i] == target) return true;
    }
    return false;
}


```

```java

public static boolean search(Node head, int target){
      Node temp = head;
      while(temp != null){
          if(temp.val == target) return true;
          temp = temp.next;
      }
     return false;
}

```

## DRY RUN:

<img width="1397" alt="Search element in linked list" src="https://github.com/user-attachments/assets/ba140775-f87a-407e-903f-0d178f2d3145" />

