# Agenda

### Prefix Sum
Given an array of size N, create its prefix sum array.
```java
int[] arr = [1, 2, 3, 4, 5]
int[] prefixSum = [1, 3, 6, 10, 15]
```

Let's dive deep into this **Problem Solving Technique** to understand it more thoroughly.

```java
prefixSum[0] = arr[0] = 1
prefixSum[1] = arr[0] + arr[1] = 1 + 2 = 3
prefixSum[2] = arr[0] + arr[1] + arr[2] = 1 + 2 + 3 = 6
prefixSum[3] = arr[0] + arr[1] + arr[2] + arr[3] = 1 + 2 + 3 + 4 = 10
prefixSum[4] = arr[0] + arr[1] + arr[2] + arr[3] + arr[4] = 1 + 2 + 3 + 4 + 5 = 15
```
![prefix sum brute force](https://github.com/user-attachments/assets/7fe5d5a4-2c86-4ddb-a9e3-ad1eaea3820a)

In this case, we are repeatedly adding the previous value to the prefix sum array.
So, let's apply **Prefix Sum Technique** to solve the problem.

In general, we are repeatedly adding the previous array values, so we can break that down into the previous **Prefix Sum  + Current Value**.

```java
prefixSum[0] = arr[0] = 1
prefixSum[1] = prefixSum[0] + arr[1] = 1 + 2 = 3
prefixSum[2] = prefixSum[1] + arr[2] = 3 + 3 = 6
prefixSum[3] = prefixSum[2] + arr[3] = 6 + 4 = 10
prefixSum[4] = prefixSum[3] + arr[4] = 10 + 5 = 15
```
![prefix sum optimized](https://github.com/user-attachments/assets/3c827864-b6a1-495f-84c1-4984b54c7858)
#### Prefix Sum Formula
```
prefixSum[i] = prefixSum[i-1] + arr[i]
```
So, the prefix sum array would look like this: If you want to find the sum of a particular range, you can easily calculate it.
```
int[] prefixSum = [1, 3, 6, 10, 15]
```
Let's say we have the scores of the Indian cricket team for the first 10 overs in an array:
```
    overs =   1   2   3   4   5   6   7   8   9  10
prefixSum = [ 4, 15, 22, 32, 45, 56, 67, 83, 88, 91 ]

```
Given an array of size 10, to find the score of the Indian team for a particular over, let's say the 5th over, I can calculate the total score from the 1st to 4th over and subtract the score of the 5th over to get the score for the 5th over, right?"

```
5th over ---->  45 - 32 = 13 , so prefixSum[5] - prefixSum[4]
4th over to 6th over -----> 56 - 22 = 34, prefixSum[6] - prefixSum[3]
```
### How to Use the Prefix Sum Array for Range Sum Queries:
Once we have the prefix sum array, we can quickly compute the sum of any subarray arr[l...r] (where l is the starting index and r is the ending index) using the following formula:
So In general **Formula** is
```java
prefixSum[r] - prefixSum[l-1]
```

### Edge Case:
If you want to get the score from the 0th to the 5th over, you can simply look at the value at the 5th index in the prefix sum array.
In this case you want find out the edge case
```java
l = 0;
r = 5;
if(l == 0){
   sum(l, r) = prefixSum[r]
}else {
    sum(l, r) = prefixSum[r] - prefixSum[l-1]
}

```
## Brute Force Approach of Range Sum Queries:

- **TC**: $O(Q * N)$
- **SC**: O(1)

```java
int[] arr = {1, 2, 3, 4, 5, 6, 7, 8};
int[][] query = { {0,3}, {2, 5}, {1, 4}, {3,6}, {0,7} };
rangeSum(arr, query);
```
```java
public static void rangeSum(int[] arr, int[][] query){    
    int Q = query.length;

    for(int i = 0; i < Q; i++){
        int L = query[i][0],  R = query[i][1];
        int sum = 0;
        for(int j = L; j <= R; j++){
          sum += arr[j];
        }
        System.out.print(sum + " ");
    }
}

```

## Optimized Approach for Range Sum Queries:

- **TC**: `O(N + Q)`
- **SC**: `O(N)`  - Because of the Prefix Sum, we can further optimize the space by using in-place techniques.

```java
int[] arr = {1, 2, 3, 4, 5, 6, 7, 8};
int[][] query = { {0,3}, {2, 5}, {1, 4}, {3,6}, {0,7} };
rangeSum(arr, query);
```

```java
 public static void rangeSum(int[] arr, int[][] query){    

    int Q = query.length;
    int N = arr.length;
    int[] prefixSum = new int[N];

    prefixSum[0] = arr[0];

    for(int i = 1; i < N; i++){
      prefixSum[i] = prefixSum[i - 1] + arr[i];
    }
    
    for(int i = 0; i < Q; i++){
        int L = query[i][0],  R = query[i][1];
        int sum = 0;

        if(L == 0){
          sum += prefixSum[R];
        }else {
          sum += prefixSum[R] - prefixSum[L - 1];
        }
       
      System.out.print(sum + " ");
    }
  }
```

#### In-place Technique of Prefix Sum:

- **TC**: `O(N + Q)`
- **SC**: `O(1)`

  
```java
int[] arr = {1, 2, 3, 4, 5, 6, 7, 8};
int[][] query = { {0,3}, {2, 5}, {1, 4}, {3,6}, {0,7} };
rangeSum(arr, query);
```

```java
 public static void rangeSum(int[] arr, int[][] query){    

    int Q = query.length;
    int N = arr.length;

    for(int i = 1; i < N; i++){
      arr[i] = arr[i - 1] + arr[i];
    }
    
    for(int i = 0; i < Q; i++){
        int L = query[i][0],  R = query[i][1];
        int sum = 0;

        if(L == 0){
          sum += arr[R];
        }else {
          sum += arr[R] - arr[L - 1];
        }
       
      System.out.print(sum + " ");
    }
  }
```
## Even Indices Range Sum Queries:


### Brute Force:

- **TC**: $O(Q * N)$
- **SC**: O(1)

```java
int[] arr = {1, 2, 3, 4, 5, 6, 7, 8};
int[][] query = { {0,3}, {2, 5}, {1, 4}, {3,6}, {0,7} };
evenIndicesRangeSum(arr, query);
```

```java
public static void evenIndicesRangeSum(int[] arr, int[][] query){
    int Q = query.length;
    for(int i = 0; i < Q; i++){
        int L = query[i][0], R = query[i][1];
        int sum = 0;
        for(int j = L; j <= R; j++){
            if(j % 2 == 0){
                sum += arr[j];  
            }
        }
        System.out.print(sum + " ");
    }
}
```

### Optimized:

- **TC**: $O(N + Q)$
- **SC**: O(N)

```java
int[] arr = {1, 2, 3, 4, 5, 6, 7, 8};
int[][] query = { {0,3}, {2, 5}, {1, 4}, {3,6}, {0,7} };
evenIndicesRangeSum(arr, query);
```

```java
public static void evenIndicesRangeSum(int[] arr, int[][] query){
    int Q = query.length;
    int N = arr.length;
    int[] prefixSum = new int[N];
    prefixSum[0] = arr[0];
    for(int i = 1; i < N; i++){
        if(i % 2 == 0){
            prefixSum[i] = prefixSum[i - 1] + arr[i];
        }else {
            prefixSum[i] = prefixSum[i - 1];
        }    
    }
    for(int i = 0; i < Q; i++){
        int L = query[i][0], R = query[i][1];
        int sum = 0;
        if(L == 0){
            sum += prefixSum[R];
        }else {
            sum += prefixSum[R] - prefixSum[L - 1];
        }
        System.out.print(sum + " ");
    }
}
```
## Equilibrium index :

### ❓ Question:
You are given an array A of integers of size N.
Your task is to find the equilibrium index of the given array
The equilibrium index of an array is an index such that the sum of elements at lower indexes is equal to the sum of elements at higher indexes.
If there are no elements that are at lower indexes or at higher indexes, then the corresponding sum of elements is considered as 0.

### Problem Constraints:


1 ≤ N ≤ $10^5$

$-10^5$ ≤ A[i] ≤ $10^5$


```java
int[] A = {-7, 1, 5, 2, -4, 3, 0}
```

```java
int[] A = {-7, 1, 5, 2, -4, 3, 0};
System.out.println(edbrium(A));
```
## Brute Force:

- **TC**: $O(N^2)$
- **SC**: O(1)

Given the constraints $10^5$ and $10^5 \times 10^5 = 10^{10}$, the brute force approach will result in a **Time Limit Exceeded (TLE)** error because $10^{10} > 10^8$.


```java
public static int edbrium(int[] A){
      int N = A.length;

      for(int i = 0; i < N; i++){
        int leftSum = 0;
        for(int j = 0; j < i; j++){
          leftSum += A[j];
        }
        int rightSum = 0;
        for(int k = i + 1; k < N; k++){
          rightSum += A[k];
        }
        if(leftSum == rightSum){
          return i;
        }
      }
      return -1;
  }
```

## Optimized:

- **TC**: $O(N)$
- **SC**: O(N) - Because of Prefix sum array

```java
int[] A = {-7, 1, 5, 2, -4, 3, 0}
```

```java
int[] A = {-7, 1, 5, 2, -4, 3, 0};
System.out.println(edbrium(A));
```

![Equalibrium optimized](https://github.com/user-attachments/assets/a6e21705-a23a-41dd-8f7a-9d016e1ff0ca)


```java
public static int edbrium(int[] A){
    int N = A.length;
    prefixSum[0] = A[0];
    for(int i = 0; i < N; i++){
        prefixSum[i] = prefixSum[i - 1] + A[i];
    }
    for(int i = 0; i < N; i++){
        int leftSum = 0, rightSum = 0;
        if(i != 0){
            leftSum = prefixSum[i - 1];
        }
        rightSum = prefixSum[n - 1] - prefixSum[i];
        if(leftSum  == rightSum) {
            return i;
        }
    }
    return -1;
}
```

## Without Prefix Sum - Equalibrium:

- **TC**: $O(N)$
- **SC**: O(1)

```java
int[] A = {-7, 1, 5, 2, -4, 3, 0};
System.out.println(edbrium(A));
```

```java
public static int edbrium(int[] A){
    int N = A.length;
    int leftSum = 0, rightSum = 0, pivot = 0;

    // Calculate the right sum
    for(int i = 1; i < N; i++){
        rightSum += A[i];
    }

     // Iterate pivot over all the elements of the array
    // and until left != right
    while(pivot < N - 1 && leftSum != rightSum){
        pivot++;
        rightSum -= A[pivot];
        leftSum += A[pivot - 1]; 
    }
    // If leftSum == rightSum, return pivot as the equilibrium index
    if(leftSum == rightSum){
        return pivot;
    }
    return -1;
}
```
