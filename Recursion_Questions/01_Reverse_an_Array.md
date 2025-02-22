# Reverse an Array using Recursion

## Java Implementation

```java
class ReverseArrayRecursion {
    // Recursive method to reverse the array
    public static void recursiveArray(int[] arr, int lb, int ub) {
        if (lb >= ub) {
            return; // Base case: When left index meets or crosses right index
        }
        
        // Swap elements at lb and ub
        int temp = arr[lb];
        arr[lb] = arr[ub];
        arr[ub] = temp;

        // Recursive call moving indices inward
        recursiveArray(arr, lb + 1, ub - 1);
    }
    
    // Method to print the array
    public static void printArray(int[] arr){
        for(int i:arr){
            System.out.print(i + " | ");
        }
        System.out.println();
    }

    public static void main(String[] args) {
        int[] arr = {10, 12, 14, 34, 22};
        System.out.println("Original Array:");
        printArray(arr);

        recursiveArray(arr, 0, arr.length - 1);

        System.out.println("Reversed Array:");
        printArray(arr);
    }
}
```

## Explanation

### How it Works
1. **Base Case**: The recursion stops when `lb >= ub`, meaning the left and right indices have met or crossed.
2. **Swapping Elements**:
   - The first and last elements are swapped.
   - The second and second-last elements are swapped, and so on.
3. **Recursive Call**:
   - The function calls itself with updated indices: `lb + 1` and `ub - 1`.
   - This process continues until the base case is reached.

### Example Execution
#### Input:
```
arr = {10, 12, 14, 34, 22}
```

#### Step-by-Step Execution:
| Step | `lb` | `ub` | Swap (`arr[lb] ↔ arr[ub]`) | Updated Array |
|------|------|------|------------------|---------------|
| 1    | 0    | 4    | 10 ↔ 22          | `{22, 12, 14, 34, 10}` |
| 2    | 1    | 3    | 12 ↔ 34          | `{22, 34, 14, 12, 10}` |
| 3    | 2    | 2    | Stop (Base Case) | `{22, 34, 14, 12, 10}` |

#### Output:
```
Reversed Array: {22, 34, 14, 12, 10}
```

## Complexity Analysis
- **Time Complexity:** `O(N)`, as each element is swapped once.
- **Space Complexity:** `O(N)`, due to recursive function calls on the stack.

### Alternative Approach
- **Iterative Approach:**

```java

import java.util.Scanner;

public class ReverseArray {
    
    // Method to reverse and print an array
    public static void reverseArray(int[] arr) {
        System.out.println("The reversed array: ");
        for (int j = arr.length - 1; j >= 0; j--) {
            System.out.print(arr[j] + " | ");
        }
        System.out.println();
    }

    public static void main(String[] args) {
        Scanner input = new Scanner(System.in);
        
        // Taking array size input
        System.out.print("Enter the size of the array: ");
        int size = input.nextInt();
        
        int[] arr = new int[size];

        // Taking array elements input
        System.out.print("Enter the elements: ");
        for (int i = 0; i < arr.length; i++) {
            arr[i] = input.nextInt();
        }

        reverseArray(arr);

        // Closing the scanner to prevent resource leaks
        input.close();
    }
}
