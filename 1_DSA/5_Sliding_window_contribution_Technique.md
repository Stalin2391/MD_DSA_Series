# Agenda

### Contribution Technique
### Sliding Window

-----

## Question:

Given an array 𝐴 of size 𝑁, write a program to find the **sum of all subarrays** of the array. A subarray is any contiguous segment of the array.

## Brute Force Idea:

We can iterate over all possible subarrays of the given array and compute the sum for each subarray individually

#### Idea 1:

- **TC**: $O(N^{3})$
- **SC**: O(1)


```java

int[] A = {3, 2, 1, 4, 7, 9};
System.out.print(sumOfAllSubArr(A));

```

```java

public static int sumOfAllSubArr(int[] arr){
    int N = arr.length;
    int totalSum = 0;
    for(int i = 0; i < N; i++){
        for(int j = i; j < N; j++){
            int sum = 0;
            for(int k = i; k <= j; k++){
                sum += arr[k];
            }
            totalSum += sum;
        }
    }
    return totalSum;
}


```

#### Idea 2:


- **TC**: $O(N^{2})$
- **SC**: O(1)

```java

public static int sumOfAllSubArr(int[] arr){
    int N = arr.length;
    int totalSum = 0;
    for(int i = 0; i < N; i++){
        int sum = 0;
        for(int j = i; j < N; j++){
            sum += arr[j];
            totalSum += sum;
        }
    }
    return totalSum;    
}

```

## Contribution Technique

- **TC**: $O(N)$
- **SC**: O(1)


```java

int[] A = {3, 2, 1, 4, 7, 9};
System.out.print(sumOfAllSubArr(A));

```

![Screenshot 2025-01-02 at 09 43 33](https://github.com/user-attachments/assets/57a2da0a-b309-4317-812f-79a4bcdacdf3)


### Formula: 

- **(i+1):** Number of subarrays that start from index 0 to \(i\).
- **(N-i):** Number of subarrays that end at index \(i\) and go until the end of the array.

For ***ith Index*** is `(i + 1) (N - i)`


```java

public static int sumOfAllSubArrContribution(int[] arr){
    int N = arr.length;
    int totalSum = 0;
    
    for(int i = 0; i < N; i++){
        int freq = (i + 1) * (N - i);
        int contribution = arr[i] * freq;
        totalSum += contribution;
    }
    
    return totalSum;
}


```


### Dry Run : 

The contribution technique involves calculating the contribution of each element in the array to the total sum of all subarrays, then multiplying it by the number of times that element appears in all possible subarrays.Count the Each elements contribution and multiply with their contribution

![Screenshot 2025-01-02 at 09 43 53](https://github.com/user-attachments/assets/2a66e328-d8bb-406b-8ab2-3c8c51ed6960)
