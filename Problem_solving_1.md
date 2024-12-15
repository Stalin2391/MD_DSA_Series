# Content

### Factors
### Prime Numbers
### Basic Math Revision
### Number of Iteration


# Factors
    -> We can say  ( i ) is a factor of N, i divides N completely remainder is Zero ( 0 ).

### ❓Question:
    Given N, return number of factors of N. 

### 💬 Answer:
    -> Example : 

    ❓ Q1: Number of factors of 24 => [ 1, 2, 3, 4, 6, 8, 12, 24] => Total number of Factors is 8.

    ❓ Q1: Number of factors of 10 => [ 1, 2, 5, 10] => Total number of Factors is 4.

    - Minimum Factor of N is 1.

    - Maximum Factor of N is N => ( Number itself).

## Code 💻

### Brute force Approach:

_TC_ : O(N)  
_SC_ : O(1)

```java
function count_factors( int N ){

    int freq_count = 0;

    for(int i = 1; i <= N; i++){

        if( N % i == 0 ){

            freq_count++;
        }
    }

    return freq_count;
}
```
### Optimized Approach:

_TC_ : O(sqrt(N))  
_SC_ : O(1)

```java
function count_factors(int N) {
    int freq_count = 0;

    for (int i = 1; i * i <= N; i++) {
        if (N % i == 0) { 
            if (N / i == i) {
                freq_count++; 
            } else {
                freq_count += 2; 
            }
        }
    }

    return freq_count;
}

