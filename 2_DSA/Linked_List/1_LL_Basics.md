# Agenda 
### Linked List Basics
### Search for element x
### Insert / Delete of any Node 
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


## DRY RUN: 

<img width="1445" alt="Beginning of a Linked List" src="https://github.com/user-attachments/assets/96e60003-bb2d-4a05-bff6-8368a49a38c3" />

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

<img width="1433" alt="Delete in position" src="https://github.com/user-attachments/assets/b770b0f1-9fbf-466a-a734-4e7f8c46a17c" />

If O - th Node Deleted the output would be :

output : 2 -> 3 -> 4 -> 5


### DRY RUN: Delete the B-th Node from the linked list:

<img width="1423" alt="Delete Edge case" src="https://github.com/user-attachments/assets/a39f9980-cbee-489c-94a2-4bacd19fb68e" />

If B - th Node (B = 3) Deleted the output would be :

output : 1 -> 2 -> 3 -> 5


# Search for element x

Given a target x iterate and check if **Target** exists or not?. 

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

