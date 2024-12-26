# Agenda
#### Binary Search


----


#### ❓ Question 1:

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

<div style="margin-bottom : 15px; padding: 15px; border: 2px solid #81C784; border-radius: 5px;">
  <strong style="color: #388E3C; font-size: 18px;">Note:</strong>

🔹 **Target**  
🔸 **Search space**  
🔵 **Condition**

</div>

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
```

#### ❓ Question 2:

Find the first occurrence of an element in a sorted array

## Brute Force:

_TC_ : O(N)  
_SC_ : O(1)

```java

int[] arr = {1, 2, 2, 2, 3, 4, 5};
int k = 2;
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

#### ❓ Question 3:

Everey elements occures twice except for one. Find the unique element. Duplicate elements are adjacent to each other but array is not sorted.

#### Brute force:


> _TC_ : $O(N^2)$  
> _SC_ : O(1)

```java

int[] arr = {8, 8, 5, 5, 6, 2, 2};
uniqueElement(arr);

```
```java
public static int uniqueElement(int[] arr){
    int N = arr.length;

    int ans = 0;
    for(int i = 0; i < N; i++){
        boolean isUnique = true;
        for(int j = 0; j < N; j++){
            if(i != j && arr[i] == arr[j]){
                isUnique = false;
                break;
            }
        }

        if(isUnique){
            ans = arr[i];
        }
    }
    return ans;
}
```

#### Better:

> _TC_ : $O(N)$  
> _SC_ : O(1)

```java

int[] arr = {8, 8, 5, 5, 6, 2, 2};
uniqueElement(arr);

```

```java
public static int uniqueElement(int[] arr){
    int N = arr.length;
    HashMap<Integer, Integer> map = new HashMap<>();

    for(int i = 0; i < N; i++){
        if(map.containsKey(arr[i])){
            int val = map.get(arr[i]);
            map.put(arr[i], val + 1);
        }else {
            map.put(arr[i],  1);
        }
    }
    int ans = 0;
    for(int i = 0; i < N; i++){
        if(map.get(arr[i]) == 1){
            ans = arr[i];
        }
    }
    return ans;
}

```