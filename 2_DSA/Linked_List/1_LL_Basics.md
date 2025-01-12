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

