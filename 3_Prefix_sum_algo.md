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
