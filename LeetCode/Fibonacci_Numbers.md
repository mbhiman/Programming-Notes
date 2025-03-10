# Fibonacci Series and Optimized Implementations

## What is the Fibonacci Series?
The Fibonacci series is a sequence of numbers where each number is the sum of the two preceding ones, starting from 0 and 1:

```
0, 1, 1, 2, 3, 5, 8, 13, 21, 34, ...
```

Mathematically, it is defined as:
- **Base cases:**
  - `F(0) = 0`
  - `F(1) = 1`
- **Recursive formula:**
  - `F(n) = F(n-1) + F(n-2)`, for `n ≥ 2`

## Fibonacci Using Recursion
A simple way to compute the Fibonacci sequence is using recursion:

```java
class Solution {
    public int fib(int n) {
        if (n == 0 || n == 1) {
            return n;
        }
        return fib(n - 1) + fib(n - 2);
    }
}
```

### Advantages of Recursion:
  
  ✅ **Easy to understand and implement**
  ✅ **Follows the mathematical definition closely**

### Disadvantages of Recursion:

  ❌ **Exponential time complexity O(2^n), leading to a lot of redundant calculations**
  ❌ **Leads to stack overflow for large `n` due to deep recursion calls**
  ❌ **Very slow for large `n`**

## Optimized Fibonacci Implementations
### **1. Bottom-Up (Tabulation) - O(n) Time, O(n) Space**
This approach uses dynamic programming to store previously computed Fibonacci numbers, avoiding redundant calculations.

```java
class Solution {
    public int fib(int n) {
        if (n == 0) return 0;
        int[] dp = new int[n + 1];
        dp[0] = 0;
        dp[1] = 1;
        
        for (int i = 2; i <= n; i++) {
            dp[i] = dp[i - 1] + dp[i - 2];
        }
        return dp[n];
    }
}
```
  
  ✅ **Time Complexity:** O(n) (each Fibonacci number is computed once)  
  ✅ **Space Complexity:** O(n) (stores all values in an array)

### **2. Iterative (Space Optimized) - O(n) Time, O(1) Space**
Instead of storing all previous values, we only keep the last two numbers, reducing space complexity to O(1).

```java
class Solution {
    public int fib(int n) {
        if (n == 0) return 0;
        int a = 0, b = 1, c;
        
        for (int i = 2; i <= n; i++) {
            c = a + b;
            a = b;
            b = c;
        }
        return b;
    }
}
```

  ✅ **Time Complexity:** O(n)  
  ✅ **Space Complexity:** O(1) (only three variables are used)

## Which Approach to Use?
| Approach | Time Complexity | Space Complexity | Best For |
|----------|----------------|------------------|----------|
| Recursion | O(2^n) | O(n) (stack space) | Not recommended for large `n` |
| Bottom-Up DP | O(n) | O(n) | When `n` is small to medium |
| Iterative | O(n) | O(1) | Best for large `n`, optimal performance |

### Conclusion:
- **Avoid naive recursion** due to exponential time complexity.
- **Use Bottom-Up DP for readability** and ease of understanding.
- **Use Iterative (O(1) space) for real-world performance.**

🚀 *For competitive programming and large `n`, always use the iterative O(1) space approach.*

