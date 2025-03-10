# Palindrome String Check in Java

## What is a Palindrome?
A **palindrome** is a word, phrase, number, or sequence of characters that **reads the same forward and backward** after removing non-alphanumeric characters and converting all uppercase letters to lowercase.

### **Examples of Palindromes:**
- **Words:** "madam", "racecar", "level"
- **Phrases (Ignoring Spaces and Punctuation):** "A man, a plan, a canal: Panama", "No lemon, no melon"
- **Numbers:** 121, 12321, 9999

## **How to Check if a String is a Palindrome in Java**
### **Approach**
To check if a given string is a palindrome, follow these steps:
1. **Convert the string to lowercase** to ensure case insensitivity.
2. **Remove all non-alphanumeric characters** (such as spaces, punctuation, and symbols).
3. **Use two pointers (left and right):**
   - Compare characters from the beginning (`lb`) and end (`ub`).
   - Move pointers inward after every successful comparison.
   - If a mismatch is found, return `false`.
   - If pointers cross without mismatches, return `true`.

### **Java Solution (13ms Runtime on LeetCode)**
```java
class Solution {
    public boolean isPalindrome(String s) {
        // Convert to lowercase and remove non-alphanumeric characters
        s = s.toLowerCase().replaceAll("[^a-z0-9]", "");
        
        int lb = 0;
        int ub = s.length() - 1;
        
        while(lb < ub){
            if(s.charAt(lb) != s.charAt(ub)){
                return false;
            }
            lb++;
            ub--;
        }
        return true;
    }
}
```

## **Explanation of Code:**
- `s.toLowerCase()` → Converts the string to lowercase.
- `s.replaceAll("[^a-z0-9]", "")` → Removes all non-alphanumeric characters.
- `while(lb < ub)` → Loops until the left pointer (`lb`) crosses the right pointer (`ub`).
- `s.charAt(lb) != s.charAt(ub)` → If characters don’t match, return `false`.
- If the loop completes, return `true` (the string is a palindrome).

## **Time & Space Complexity Analysis**
| Complexity | Explanation |
|------------|-------------|
| **Time Complexity** | **O(n)** (String traversal and character comparisons) |
| **Space Complexity** | **O(n)** (Creating a new string after removing non-alphanumeric characters) |

## **Optimizing for Better Performance**
- Instead of `replaceAll()`, use `Character.isLetterOrDigit()` to filter characters in **O(1)** space.
- This reduces the need for extra memory allocation.

### **Optimized Two-Pointer Approach (Faster Execution)**
```java
class Solution {
    public boolean isPalindrome(String s) {
        int lb = 0, ub = s.length() - 1;
        
        while (lb < ub) {
            while (lb < ub && !Character.isLetterOrDigit(s.charAt(lb))) {
                lb++; // Skip non-alphanumeric characters
            }
            while (lb < ub && !Character.isLetterOrDigit(s.charAt(ub))) {
                ub--; // Skip non-alphanumeric characters
            }
            if (Character.toLowerCase(s.charAt(lb)) != Character.toLowerCase(s.charAt(ub))) {
                return false;
            }
            lb++;
            ub--;
        }
        return true;
    }
}
```

### **Advantages of the Optimized Version:**
- Avoids extra memory allocation (`O(1) space` complexity).
- Efficient string traversal with **two pointers**.
- Faster execution (~2ms on LeetCode compared to 13ms).

