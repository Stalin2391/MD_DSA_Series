# Agenda
#### Binary Search


------------------------------------------------------------


#### ❓ Question:

Given an array of size N, find the index of the element k. If k is present in the array, return its index. If k is not found in the array, return -1.

## Brute Force:

_TC_ : O(N)  
_SC_ : O(1)

```java

int[] arr = {2, 3, 4, 10, 40};
int k = 10;
findIndex(arr, k);

```

```java

public static int findIndex(int[] arr, int k){
    int N = arr.length;

    for(int i = 0; i < N; i++){
        if(arr[i] == k){
            return i;
        }
    }

    return -1;
}

```


## Binary Search Algorithm:

### Optimized Approach:

_TC_ : O(log N)  
_SC_ : O(1)

```java

int[] arr = {2, 3, 4, 10, 40};
int k = 10;
findIndex(arr, k);

```

Note:
    - Target
    - search space
    - condition

```java
public static int findIndex(int[] arr, int k){

    int N = arr.length;
    int l = 0, h = N - 1;

    while(l <= h){
        int mid = l + (h - l) / 2;

        if(arr[mid] == k){
            return mid;
        }

        if(arr[mid] < k){
            l = mid + 1;
        }else {
            h = mid - 1;
        }
    }

    return -1;
}