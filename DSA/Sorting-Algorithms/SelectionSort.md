# Selection Sort 

Selection sort is a sorting algorithm that selects the smallest element from an unsorted list in each iteration and places that element at the beginning of the unsorted list.

## Working Principle of Selection Sort

1.  Find the smallest element in the array.
2.  Swap it with the first element.
3.  Move to the next position and find the next smallest element.
4.  Repeat until the entire array is sorted.

## Algorithm (Steps)

1.  Start from the first index (i = 0).
2.  Find the minimum element in the remaining unsorted portion ( i+1 to n-1 ).
3.  Swap this minimum element with the element at index i.
4.  Move to the next index (i = 1) and repeat the process until the array is sorted.\

## Java Implementation 

```Java
class SelectionSort {
    public static void selectionAlgo(int[] arr){
        int n = arr.length;

        for(int i = 0; i < arr.length - 1; i++){
            int minIndex = i;

            // Find the minimum element in the unsorted part
            for(int j = i+1; j<arr.length; j++){
                if(arr[j] < arr[minIndex]){
                    minIndex = j;
                }
            }
                // Swap the found minimum element with the first element
                int temp = arr[i];
                arr[i] = arr[minIndex];
                arr[minIndex] = temp;
        }
        for(int i: arr){
            System.out.print(i + " | ");
        }
    }

    public static void main(String[] args){
        int[] array = {10, 9, 12, 4, 15};
        selectionAlgo(array);
    }
}
```
## Selection Sort Execution

### **Initial Array**
10  9  12  4  15

### **Stepwise Execution of Selection Sort**

| Step  | Array State              |
|-------|--------------------------|
| Start | **10  9  12  4  15**      |
| Pass 1 | **4**  9  12  **10**  15  |
| Pass 2 | 4  **9**  12  10  15  |
| Pass 3 | 4  9  **10**  12  15  |
| Pass 4 | 4  9  10  **12**  15  |
| End   | 4  9  10  12  15  |

### **Final Sorted Array**
4  |  9  |  |  10  |  12  |  15

### Time Complexity
| Case        | Complexity |
|------------|------------|
| Best Case (Already Sorted) | **O(n²)** |
| Worst Case (Reversed Order) | **O(n²)** |
| Average Case | **O(n²)** |

- Selection Sort always runs in **O(n²)** time as it scans the entire unsorted portion to find the minimum in each pass.
- It performs **(n-1) + (n-2) + ... + 1 = O(n²)** comparisons.

### Space Complexity
- **O(1) (Constant Space)**  
- **Selection Sort is an in-place sorting algorithm**, meaning it does not use extra space beyond the given array.

### Advantages
✅ **Simple and easy to implement**  
✅ **Works well for small datasets**  
✅ **Performs fewer swaps compared to Bubble Sort**  

### Disadvantages
❌ **Not efficient for large datasets (O(n²) complexity)**  
❌ **Does not take advantage of partially sorted data**  
❌ **Slower than other algorithms like Quick Sort, Merge Sort, or Heap Sort**  

### When to Use Selection Sort?
- When the **array size is small**.  
- When **memory (space) is limited**, since it sorts in-place.  
- When **swaps are expensive**, as Selection Sort minimizes the number of swaps.  
