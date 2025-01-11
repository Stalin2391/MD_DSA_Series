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

public static search(Node head, int target){
      Node temp = head;
      while(temp != null){
          if(temp.val == target) return true;
          temp = temp.next;
      }
     return false;
}

```


