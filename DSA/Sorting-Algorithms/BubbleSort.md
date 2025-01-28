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
```

# When to Use Bubble Sort

Bubble Sort is a simple sorting algorithm, but it is often considered inefficient for large datasets. It compares and swaps adjacent elements until the array is sorted. Despite its simplicity, it has limitations that make it less suitable for larger or more complex data structures.

## When to Use Bubble Sort:
1. **Small Data Sets**:
   - Bubble Sort can be useful for small arrays where the overhead of more complex algorithms (like Quick Sort or Merge Sort) is not justified. For small arrays, the simplicity of Bubble Sort can sometimes outweigh its inefficiency.

2. **Educational Purpose**:
   - Bubble Sort is often used in educational contexts to teach the basics of sorting algorithms and algorithmic thinking. It helps introduce key concepts like **swapping** and **comparing elements**.

3. **Partially Sorted Arrays**:
   - If you already know that the array is nearly sorted (i.e., only a few elements are out of order), Bubble Sort might be efficient because it can terminate early once no swaps are needed. This is where the **optimized version** (with the `swapped` flag) comes into play, reducing unnecessary passes.

4. **In-Place Sorting**:
   - If you need a simple, **in-place sorting algorithm** (without requiring extra memory), Bubble Sort is a good choice. It has **O(1) space complexity**, meaning it doesn’t require additional storage like Merge Sort or Quick Sort.

5. **Real-Time Constraints**:
   - In scenarios where memory usage is a bigger concern than time complexity, Bubble Sort might be used because it works directly on the input array without additional memory overhead. 

## Limitations:
- **Inefficiency**: Bubble Sort is not recommended for large datasets because of its **O(n^2)** time complexity in the worst and average cases. Other algorithms like Merge Sort or Quick Sort (with **O(n log n)** time complexity) are generally more efficient for large arrays.
- **Not Stable for Certain Use Cases**: While Bubble Sort is a stable sorting algorithm (it preserves the order of equal elements), its inefficiency makes it impractical in many real-world applications.

---

## Summary:
Use Bubble Sort for small, nearly sorted datasets or for educational purposes. For larger or more complex datasets, consider using more efficient algorithms like **Quick Sort**, **Merge Sort**, or **Insertion Sort**.

