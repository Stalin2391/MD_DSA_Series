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
```
### DRY RUN:

```java

// PART A
// i        N / i 
// 1        24 / 1 = 24
// 2        24 / 2 = 12
// 3        24 / 3 =  8
// 4        24 / 4 =  6
---------------------------------------- We Don't need to iterate all values, just iterate the PART A 
// PART B
// 6        24 / 6 =  4
// 8        24 / 8 =  3
// 12       24 / 12 = 2
// 24       24 / 24 = 1
```

```java
// i        N / i  
// 1        36
// 2        18
// 3        12
// 4         9
// 6         6  --> Edge case in this case you need to increase your count by 1 else incease count by 2.

if(N / i == i){
    count++;
}else {
    count += 2;
}

```


# Iteration - Standard Way

$10^8$ iterations -------> 1 sec.


| N        | Iteration | Execution Time |
|----------|-----------|----------------|
| $10^8$   | $10^8$    | 1 sec          |
| $10^9$   | $10^9$    | 10 sec         |
| $10^{18}$| $10^{18}$ | $10^{18}$ sec  |


### Formula

$\frac{a^m}{a^n}$

$a^{m - n}$

$\frac{10^8}{10^8}$  -->  $10^{8 - 8}$  ---> $10^0$  --> 1 sec

$\frac{10^9}{10^8}$  -->  $10^{9 - 8}$  ---> $10^1$  --> 10 sec

$\frac{10^{18}}{10^8}$  -->  $10^{18 - 8}$  ---> $10^{10}$  --> $10^{10}$ sec  -> To see the output, you would need to wait for 317 years. If you run the code, it will take multiple generations—your 5th or 6th generation may be the ones to actually see the result. This highlights the need for optimizing the code.









