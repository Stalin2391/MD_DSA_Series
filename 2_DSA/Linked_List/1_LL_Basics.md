# Agenda 
### Linked List Basics
### Search for element x
### Insert / Delete of any Node 
### Reverse the Linked List
### Deep copy
-----------


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

