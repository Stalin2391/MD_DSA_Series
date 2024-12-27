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

Find the first occurrence index of an element in a sorted array

## Brute Force:

_TC_ : O(N)  
_SC_ : O(1)

```java

int[] arr = {1, 2, 2, 2, 3, 4, 5};
int k = 2;
firstOccurrence(arr, k);

```

```java

public static int firstOccurrence(int[] arr, int k){
    int N = arr.length;

    for(int i = 0; i < N; i++){
        if(arr[i] == k){
            return i;
        }
    }

    return -1;
}

```

## Optimized Approach:

_TC_ : O(log N)  
_SC_ : O(1)

```java

int[] arr = {1, 2, 2, 2, 3, 4, 5};
int k = 2;
firstOccurrence(arr, k);

```
```java

public static int firstOccurrence(int[] arr, int k){

    int N = arr.length;
    int l = 0, h = N - 1;

    int ans = -1;

    while(l <= h){
        int mid = l + (h - l) / 2;

        if(arr[mid] == k){
            ans = mid;
            // go to left
            h = mid - 1;
        }else if(arr[mid] < k){
            l = mid + 1;
        }else {
            h = mid - 1;
        }
    }
    return ans;
}

```

#### ❓ Question 3:

Find the Last occurrence index of an element in a sorted array

## Brute Force:

_TC_ : O(N)  
_SC_ : O(1)

```java

int[] arr = {1, 2, 2, 2, 3, 4, 5};
int k = 2;
lastOccurrence(arr, k);

```

```java

public static int lastOccurrence(int[] arr, int k){
    int N = arr.length;

    for(int i = N - 1; i >= 0; i--){
        if(arr[i] == k){
            return i;
        }
    }

    return -1;
}

```

#### Optimized Approach:

> _TC_ : $O(log N)$  
> _SC_ : O(1)


```java

int[] arr = {1, 2, 2, 2, 3, 4, 5};
int k = 2;
lastOccurrence(arr, k);

```
```java
public static int lastOccurrence(int[] arr, int k){
    int N = arr.length;

    int l = 0, h = N - 1;
    int ans = -1;
    while(l <= h){
        int mid = l + (h - l) / 2;
        if(arr[mid] == k){
            ans = mid;
            l = mid + 1;
        }else if(arr[mid] < k){
            l = mid + 1;
        }else {
            h = mid - 1;
        }
    }
    return ans;
}

```

#### ❓ Question 4:

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
> _SC_ : O(N)

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

#### Best:

> _TC_ : $O(N)$  
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
        ans = ans ^ arr[i];
    }

    return ans;
}
```

#### Optimized Approach:

> _TC_ : $O(log N)$  
> _SC_ : O(1)

```java

int[] arr = {8, 8, 5, 5, 6, 2, 2};
uniqueElement(arr);

```

```java

public static int uniqueElement(int[] arr){
    int N = arr.length;

    //Edge case
    if(N == 1) return arr[0];
    if(arr[0] != arr[1]) return arr[0];
    if(arr[N - 1] != arr[N - 2]) return arr[N - 1];

    int l = 1, h = N - 2;

    while(l <= h){
        int mid = l + (h - l) / 2;

        if(arr[mid] != arr[mid - 1] && arr[mid] != arr[mid + 1]){
            return arr[mid];
        }

        int firstOccurrence = mid;

        if(arr[mid - 1] == arr[mid]){
            firstOccurrence = mid - 1;
        }

        if(firstOccurrence % 2 == 0){
            l = mid + 1;
        }else {
            h = mid - 1;
        }
    }
    return -1;
}

```
#### ❓ Question 5:

##### Given an array of N distinct elements, find **any local minima** in the array.

**Local Minima:** An element in an array that is smaller than both its neighbors.

> **Note**: The local minima should be smaller than both its neighbors.


#### Brute force:

> _TC_ : $O(N)$  
> _SC_ : O(1)

```java

int[] arr = {9, 6, 3, 4, 5, 10, 12};
findLocalMinima(arr);

```

```java

public static int findLocalMinima(int[] arr) {
    int N = arr.length;

    if(N == 1) return arr[0];
    if(arr[0] < arr[1]) return arr[0];
    if(arr[N - 1] < arr[N - 2]) return arr[N - 1];
    
    for(int i = 1; i < N - 1; i++){
        if(arr[i - 1] > arr[i] && arr[i + 1] > arr[i]){
            return i; // or return arr[i]
        }
    }

    return -1;
}

```

#### Optimized Approach:

> _TC_ : $O(log N)$  
> _SC_ : O(1)

```java

int[] arr = {9, 6, 3, 4, 5, 10, 12};
findLocalMinima(arr);

```

```java

public static int findLocalMinima(int[] arr) {
    int N = arr.length;

    if(N == 1) return arr[0];
    if(arr[0] < arr[1]) return arr[0];
    if(arr[N - 1] < arr[N - 2]) return arr[N - 1];
    
    int l = 1; int h = N - 2;
    while(l <= h){
        int mid = l + (h - l) / 2;
        if(arr[mid - 1] > arr[mid] && arr[mid + 1] > arr[mid]){
            return mid;
        }
        if(arr[mid] > arr[mid - 1]){
            h = mid - 1;
        }else {
            l = mid + 1;
        }
    }

    return -1;
}

```