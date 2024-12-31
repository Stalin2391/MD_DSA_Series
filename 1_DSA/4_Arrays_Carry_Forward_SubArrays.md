# Agenda
### "ag" Pairs
### Sub Arrays Intro
### Print all Subarrays
### Min and Max of Subarray


## Question 1: 

Count Pairs "ag": Given a char[N], Calculate no.of pairs = i,j such that i < j && ch[i] == 'a' && ch[j] == 'g'. All characters are lowercase

```java

Constraints:
1 <= N <= 10^5
'a' <= ch[i] <= 'g'

```

<img width="1276" alt="Screenshot 2024-12-29 at 20 59 33" src="https://github.com/user-attachments/assets/f2e229da-ed74-46bc-a110-23f285b788d9" />

## Brute Force Idea:

- **TC**: $O(N^{2})$
- **SC**: O(1)

<img width="1316" alt="Screenshot 2024-12-29 at 20 59 44" src="https://github.com/user-attachments/assets/4c8169fd-38e7-4f00-a69f-74f82173056b" />

```java
char[] ch = {'d', 'a', 'a', 'g', 'd', 'c', 'a', 'g'};
System.out.print(coutPairs(ch));

```

```java

public static int coutPairs(char[] ch){
    int N = ch.length;
    int count = 0;
    for(int i = 0; i < N; i++){
      if(ch[i] == 'a'){
        for(int j = i + 1; j < N; j++){
          if(ch[j] == 'g'){
            count++;
          }
        }
      }
    }
    return count;
}

```

### Optimization Idea:

<img width="1316" alt="Screenshot 2024-12-30 at 08 54 44" src="https://github.com/user-attachments/assets/7f45950a-55e8-4678-8d59-661a6c7b1850" />

#### code: Left to Right:

```java
char[] ch = {'d', 'a', 'a', 'g', 'd', 'c', 'a', 'g'};
System.out.print(coutPairs(ch));

```

```java

public static int coutPairs(char[] ch){
    int N = ch.length;
    int ans = 0;
    int ca = 0;
    for(int i = 0; i < N; i++){
      if(ch[i] == 'a'){
        ca++;
      }else if(ch[i] == 'g'){
        ans += ca;
      }
    }
    return ans;
}

```
#### code: Right to Left:

```java
public static int coutPairs(char[] ch){
    int N = ch.length;
    int ans = 0;
    int cg = 0;
    for(int i = N - 1; i >= 0; i--){
      if(ch[i] == 'g'){
        cg++;
      }else if(ch[i] == 'a'){
        ans += cg;
      }
    }
    return ans;
}

```
# Sub Arrays

### Question: Print all Sub arrays:

```java

int[] arr = {4, 2, 10, 3, 12 , -2, 15};

```
### Dry Run:
If we know the start and end indices of a subarray, we can print all the subarrays that lie between those indices.

<img width="1289" alt="Screenshot 2024-12-30 at 09 37 34" src="https://github.com/user-attachments/assets/43697c50-261c-4b8a-9862-17e64746c2b1" />

### What is Sub arrays:
- Subarrays can be visualized as contiguous part of an array, where the starting and ending indices determine the subarray.
- Single element also considered as sub array
- Array considered as sub array
- Sub array should be left to right

<img width="1118" alt="Screenshot 2024-12-30 at 09 37 19" src="https://github.com/user-attachments/assets/973e19ba-e414-4a4e-9f8e-443b0005ec81" />


### code: 

- **TC**: $O(N^{3})$
- **SC**: O(1)

```java

public void printSubArrays(int[] arr){
  int N = arr.length;
  for(int start = 0; start < N; start++){
      for(int end = start; end < N; end++){
        for(int i = start; i <= end; i++){
          System.out.print(arr[k] + " ");
        }
        System.out.println();
      }
  }
}

```

## Question: Given an array of integers, find the maximum sum of a subarray of size k

## Brute Force Idea:

- **TC**: $O(N^{2})$
- **SC**: O(1)


### code:

```java

int[] arr = {-3, 4, -2, 5, 3, -2, 8, 2, -1, 4};
int k = 5;
System.out.print(maxSubArraySum(arr, k));

```

```java

public static int maxSubArraySum(int[] arr, int k){
    int N = arr.length;
    int i = 0;
    int max_sum = 0;

    while(i <= N - k){
      int sum = 0;
      for(int j = i; j < k + i; j++){
        sum += arr[j];
      }
      max_sum = Math.max(sum, max_sum);
      i++;
    }
    return max_sum;
}

```

## Optimization idea: 

- **TC**: $O(N)$
- **SC**: O(1)

```java

int[] arr = {-3, 4, -2, 5, 3, -2, 8, 2, -1, 4};
int k = 5;
System.out.print(maxSubArraySum(arr, k));

```
### Sliding window technique:

```java

public static int maxSubArraySum(int[] arr, int k){
    int N = arr.length;
    int max_sum = Integer.MIN_VALUE;
    int sum = 0;

    for(int i = 0; i < k; i++){
      sum += arr[i];
    }

    max_sum = Math.max(sum, max_sum);

    for(int i = 1; i < N - k; i++){
      sum = sum - arr[i - 1] + arr[k + i - 1];
      max_sum = Math.max(sum, max_sum);
    }

    return max_sum;
}

```

## Question: Given an integer array arr[], find the contiguous subarray (containing at least one number) that has the largest sum and return the sum.


```java

int[] arr = {-2, 1, -3, 4, -1, 2, 1, -5, 4};
System.out.print(maxSubArrSum(arr));

```

### Brute force idea:

#### Idea 1:

- **TC**: $O(N^{3})$
- **SC**: O(1)

```java

public static int maxSubArrSum(int[] arr){
  int N = arr.length;
  int max_sum = 0;
  for(int i = 0; i < N; i++){
    for(int j = i; j < N; j++){
       int sum = 0;
       for(int k = i; k <= j; k++){
          sum += arr[k];
       }
       max_sum = Math.max(sum, max_sum);
    }
  }
  return max_sum;
}

```

#### Idea 2:

- **TC**: $O(N^{2})$
- **SC**: O(1)

```java

public static int maxSubArrSum(int[] arr){
  int N = arr.length;
  int max_sum = 0;
  for(int i = 0; i < N; i++){
    int sum = 0;
    for(int j = i; j < N; j++){
      sum += arr[j];
      max_sum = Math.max(sum, max_sum);
    }
  }
  return max_sum;
}

```

## Optimization idea: 

- **TC**: $O(N)$
- **SC**: O(1)

```java

int[] arr = {-2, 1, -3, 4, -1, 2, 1, -5, 4};
System.out.print(maxSubArrSum(arr));

```
### Kadane’s Algorithm:

```java 

public static int maxSubArrSum(int[] arr){

  int N = arr.length;
  int sum = 0;
  int max_sum = Integer.MIN_VALUE;
  for(int i = 0; i < N; i++){
    sum += arr[i];
    max_sum = Math.max(sum, max_sum);
    if(sum < 0){
      sum = 0;
    }
  }
  return max_sum;
}
```

# Question:

Find the least length of a subarray that contains both the minimum and maximum elements in an array

### Brute force idea:

- **TC**: $O(N^{3})$
- **SC**: O(1)

```java

int[] arr = {1, 3, 2, 7, 9, 5, 0, 3};
System.out.print(leastLengthSubarrayWithMinMax(arr));

```

```java
 public static int leastLengthSubarrayWithMinMax(int[] arr) {
    int N = arr.length;
    int minEle = Integer.MAX_VALUE;
    int maxEle = Integer.MIN_VALUE;

    for(int i = 0; i < N; i++){
      if(arr[i] > maxEle){
        maxEle = arr[i];
      }
      if(arr[i] < minEle){
        minEle = arr[i];
      }
    }

    int minLength = Integer.MAX_VALUE;

    for(int i = 0; i < N; i++){
      for(int j = i; j < N; j++){
        boolean isMin = false;
        boolean isMax = false;
        for(int k = i; k <= j; k++){
          if(arr[k] == minEle) isMin = true;
          if(arr[k] == maxEle) isMax = true;
          if(isMax && isMin) break;
        }
       if(isMin && isMax) minLength = Math.min(minLength, j - i + 1);
      }
    }
    return maxLength;
 }

 ```