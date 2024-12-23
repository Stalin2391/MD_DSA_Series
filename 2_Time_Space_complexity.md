# Agenda:
### Log Basics
### Calculating Iterations
### Intro to Big (O) on how to calculate it.
### Time Complexity
### Spcae Complexity


## Basics of logs:

#### What is log ? 
Inverse of Exponential function.
The logarithm of \( a \) to the base \( b \) is expressed as:

# Logarithm and Exponentiation

We can represent logarithms as:

$$ \log_b(a) $$

This asks: *What value do you need to raise \( b \) to in order to get \( a \)?*

---
## Perfect Square:
### ❓Question 1
*In other words, what value must we raise 2 to in order to get 64?*

$$ \log_2(64) $$

We know that:

$$ 2^6 = 64 $$

So, the answer is:

$$ \log_2(64) = 6 $$

### ❓Question 2
*In other words, what value must we raise 5 to in order to get 25?*

$$ \log_5(25) $$

We know that:

$$ 5^2 = 25 $$

So, the answer is:

$$ \log_5(25) = 2 $$

### ❓Question 3
*In other words, what value must we raise 2 to in order to get 32?*

$$ \log_2(32) $$

We know that:

$$ 2^5 = 32 $$

So, the answer is:

$$ \log_2(32) = 5 $$

## Not a Perfect Square than take floor Value

### ❓Question 4

$$ \log_2(10) $$


$$ 2^3 = 10 $$

So, the answer is:

$$ \log_2(10) = 3 $$


# Formula that you need to know for DSA:

![log formula](https://github.com/user-attachments/assets/d8a55a01-18a2-40d1-b96a-8aa6afeb5bdf)

![log general formula](https://github.com/user-attachments/assets/16a11427-332d-4015-aed8-55c37777acca)

# Iterations:

![Example Icon](https://upload.wikimedia.org/wikipedia/commons/a/a7/Java_logo.png) - Example 1:

```java
for(int i = 0; i < N; i++){    // N + 1
  System.out.print("Hello");   // N
}                              // 2N + 1
                               // In Big O Notation ---> O(N);
```

| Step                                   | Operation Description        | Count (Number of Operations) |
|----------------------------------------|------------------------------|------------------------------|
| `for (int i = 0; i < N; i++)`          | Loop initialization and check | `N + 1` (1 for init, N for checks, 1 for exiting) |
| `System.out.print("Hello");`           | Print "Hello" inside the loop | `N` (It runs N times, once per iteration) |
| End of loop                            | Closing the loop             | `2N + 1` (For N checks and N prints) |
| Big O Notation                         | Overall time complexity      | `O(N)`                       |


