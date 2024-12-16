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
public static int count_factors( int N ){

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
public static int count_factors(int N) {
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
| $10^{18}$| $10^{18}$ | $10^{10}$ sec  |


### Formula

$\frac{a^m}{a^n}$

$a^{m - n}$

$\frac{10^8}{10^8}$  -->  $10^{8 - 8}$  ---> $10^0$  --> 1 sec

$\frac{10^9}{10^8}$  -->  $10^{9 - 8}$  ---> $10^1$  --> 10 sec

$\frac{10^{18}}{10^8}$  -->  $10^{18 - 8}$  ---> $10^{10}$  --> $10^{10}$ sec  -> To see the output, you would need to wait for 317 years. If you run the code, it will take multiple generations—your 5th or 6th generation may be the ones to actually see the result. This highlights the need for optimizing the code.


# Prime Numbers

### ❓Question:
    Given N, Check the if N is Prime or Not.

### 💬 Answer:

    -> Example : 

    ❓ Q1: How many Prime Numbers are there?  => 10, 11, 23, 2, 25, 27, 31 => Total 4 Prime Numbers.


```java


// Use Factors function(code) to check the prime number or not.
 
public static boolean checkPrime(int N) {

    //If a number has exactly two factors, it is considered a prime number; otherwise, it is not a prime.....

    if(count_factors(N) == 2){

        return true;

    } else {

        return false;
    }
}

```

# Basic Math Revision

❓ **Q1: Sum of N Natural Numbers**

    ex: 1, 2, 3, 4, 5, 6, 7, 8............100.
    
### Formula

    N(N + 1) / 2

**Example Calculation:**

    100(100 + 1) / 2 ---> 50 * 101 = 5050

# Derivation of the Formula for the Sum of N Natural Numbers

The formula for the sum of the first **N natural numbers** is:  
\[
\text{Sum} = \frac{N(N + 1)}{2}
\]

Here’s how this formula is derived step by step:

---

## Step 1: Write the Sequence

Consider the first \( N \) natural numbers:  
\[
1, 2, 3, \dots, N
\]

---

## Step 2: Write the Sequence in Reverse

Reverse the order of the sequence:  
\[
N, N-1, N-2, \dots, 1
\]

---

## Step 3: Add the Two Sequences

Pair each number in the original sequence with its counterpart in the reversed sequence. Adding corresponding terms gives:  
\[
(1 + N), (2 + (N-1)), (3 + (N-2)), \dots, (N + 1)
\]

Notice that **each pair sums to \( N + 1 \)**.

---

## Step 4: Count the Number of Pairs

There are \( N \) numbers in the sequence. When paired, the total number of pairs is \( N \).

Thus, the sum of all pairs is:  
\[
\text{Sum of all pairs} = N \times (N + 1)
\]

---

## Step 5: Account for Double-Counting

Since the sum was calculated by adding two sequences (original and reversed), the actual sum of the sequence is half of this value:  
\[
\text{Sum of the sequence} = \frac{N \times (N + 1)}{2}
\]

---

## Final Formula

Thus, the formula for the sum of the first \( N \) natural numbers is:  
\[
\text{Sum} = \frac{N(N + 1)}{2}
\]

---

## Example: Derive the Sum for \( N = 5 \)

Let’s compute the sum of the first 5 natural numbers:  
- Sequence: \( 1, 2, 3, 4, 5 \)
- Pairing:  
  \[
  (1+5), (2+4), (3)
  \]
- Total of pairs:  
  \[
  (1+5) + (2+4) + 3 = 6 + 6 + 3 = 15
  \]

Using the formula:  
\[
\text{Sum} = \frac{5(5 + 1)}{2} = \frac{5 \times 6}{2} = 15
\]

This matches the manually calculated result.






