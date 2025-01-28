# Bubble Sort 

Bubble Sort is an algorithm that sorts an array from the lowest value to the highest value.

## Algorithm:
1. Go through the array, one value at a time.
2. For each value, compare the value with the next value.
3. If the value is higher than the next one, swap the values so that the highest value comes last.
4. Go through the array as many times as there are values in the array.

---

## Java Implementation

```java
public class BubbleSort {
    public static void sortingAlgo(int[] arr) {
        // Loop through the array
        for (int i = 0; i < arr.length - 1; i++) { 
            for (int j = 0; j < arr.length - i - 1; j++) {
                // Swap if the current element is greater than the next element
                if (arr[j] > arr[j + 1]) {
                    int temp = arr[j];
                    arr[j] = arr[j + 1];
                    arr[j + 1] = temp;
                }
            }
        }
        // Print the sorted array
        System.out.print("After sorting:");
        for (int i : arr) {
            System.out.print(i + "| ");
        }
    }

    public static void main(String[] args) {
        int[] arr = {10, 4, 6, 12, 14};
        System.out.print("The actual array: ");
        for (int i : arr) {
            System.out.print(i + " | ");
        }
        System.out.println();
        // Call the sorting algorithm
        sortingAlgo(arr);
    }
}
```

## Optimized Bubble Sort with `swapped` Variable

Using a **`swapped` variable** optimizes the Bubble Sort algorithm by terminating the sorting process early if no swaps are made during a complete pass, indicating the array is already sorted.

### Why use the `swapped` variable?
- **Efficiency**: It stops the algorithm early if the array is already sorted or nearly sorted.
- **Time Complexity**:
  - Worst case: \( O(n^2) \)
  - Best case: \( O(n) \) (when no swaps occur).

---

## Java Code Implementation

```java
public class BubbleSort {
    public static void sortingAlgo(int[] arr) {
        int n = arr.length;
        boolean swapped;

        // Outer loop for multiple passes
        for (int i = 0; i < n - 1; i++) {
            swapped = false;  // Reset the swapped flag for each pass
            // Inner loop for comparing adjacent elements
            for (int j = 0; j < n - i - 1; j++) {
                // Swap if the current element is greater than the next
                if (arr[j] > arr[j + 1]) {
                    int temp = arr[j];
                    arr[j] = arr[j + 1];
                    arr[j + 1] = temp;
                    swapped = true;  // Mark that a swap occurred
                }
            }
            // If no elements were swapped, the array is sorted
            if (!swapped) {
                break;
            }
        }

        // Print the sorted array
        System.out.println("After bubble sorting:");
        for (int i : arr) {
            System.out.print(i + " ");
        }
    }

    public static void main(String[] args) {
        int[] arr = {10, 4, 6, 12, 14};
        System.out.print("The actual array: ");
        for (int i : arr) {
            System.out.print(i + " ");
        }
        System.out.println();

        sortingAlgo(arr);  // Call the bubble sort function
    }
}
