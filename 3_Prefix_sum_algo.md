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
```
prefixSum[r] - prefixSum[l-1]
```

### Edge Case:
If you want to get the score from the 0th to the 5th over, you can simply look at the value at the 5th index in the prefix sum array.
In this case you want find out the edge case
```
l = 0;
r = 5;
if(l == 0){
   sum(l, r) = prefixSum[r]
}else {
    sum(l, r) = prefixSum[r] - prefixSum[l-1]
}

```
## Brute Force Approach of Range Sum Queries:

- **TC**: $O(N^2)$
- **SC**: O(1)

```
int[] arr = {1, 2, 3, 4, 5, 6, 7, 8};
int[][] query = { {0,3}, {2, 5}, {1, 4}, {3,6}, {0,7} };
rangeSum(arr, query);
```
```
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

- **TC**: `O(N)`
- **SC**: `O(N)`  - Because of the Prefix Sum, we can further optimize the space by using in-place techniques.

```
int[] arr = {1, 2, 3, 4, 5, 6, 7, 8};
int[][] query = { {0,3}, {2, 5}, {1, 4}, {3,6}, {0,7} };
rangeSum(arr, query);
```

```
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

- **TC**: `O(N)`
- **SC**: `O(1)`

  
```
int[] arr = {1, 2, 3, 4, 5, 6, 7, 8};
int[][] query = { {0,3}, {2, 5}, {1, 4}, {3,6}, {0,7} };
rangeSum(arr, query);
```

```
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
